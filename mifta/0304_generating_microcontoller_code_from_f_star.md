# How is F*/Pipit Converted to code that can run on a Microcontroller
## Overview:
- F*/Pipit can be compiled to C, OCaml, Wasm and F# [1]. For my Thesis, we are interested in how F*/Pipit can be compiled to C.
- KaRaMel (formerly known as KreMLin) is a compiler that compiled a F* Program to C Code [1], [3]

## High Level Perspective: 
From a high-level perspective, KaRaMeL takes an input AST, translates it into a typed internal AST, then massages the program by performing repeated transformations until the program fits within a simple enough subset dubbed Low*. Once a program is valid Low*, it translates almost trivially into C*, an idealized dialect of C. Then, the program is translated to an abstract C AST, and finally pretty-printed [3].
## Detailed Steps:
1. **Creating a ML-like AST as an input to KaRaMel:** F*'s existing `normalizer, eraser and extraction facility` is used to convert the F*/Pipit code to a ML-like AST [2, Section 4.1].
2. **Translating to a Typed AST:** KaRaMel takes the AST created and translates it into a typed internal AST [3].
   1. Expressions and Patterns are annotated with their types
   2. Each Node in the initial AST is now associated with type information.
3. **Re-Checking the Typed AST:** The typed-annotted OST is re-checked to ensure that the program makes sense semantically [3].
   1. Ill-Typed parts of the program may be dropped.
4. **Parametrised Type Abbreviations:** Parameterised type abbreviations are substituted with their expansion. 
   1. ***Parameterised Types:*** Take one more more parameters, allowing for the creation of generic data structures or functions. For example, a list that can hold any type of item `List<T>`, where T is the type parameter.
   2. ***Type Abbreviations:*** Shorter/custom names given to parameterised types. For example, `StringList` might be an abbreviation for `List<String>`
   3. So, this step would involve replacing all occurences of `StringList` with `List<String>`
5. **Monomorphization:** All data types go through Monomorphization. Example to explain the concept:
```rust
fn find_max<T: PartialOrd>(list: &[T]) -> T {
    let mut max = list[0];
    for &item in list.iter() {
        if item > max {
            max = item;
        }
    }
    max
}
// T is a generic type
// list: &[T] is a reference to a slice of items of type T.

fn main() {
    let integers = vec![1, 2, 3, 4, 5];
    let floats = vec![1.1, 2.2, 3.3, 4.4, 5.5];
    
    let max_int = find_max(&integers);
    let max_float = find_max(&floats);
    
    println!("The maximum integer is: {}", max_int);
    println!("The maximum float is: {}", max_float);
}
```
- When the Rust compiler encounters these calls to find_max with different types (`i32` for integers and `f64` for floats), it performs monomorphization. 
- It generates two specialized versions of find_max: one that works with `i32` and another that works with `f64`, as if we manually wrote 2 different functions 

```rust
// A version for `i32`
fn find_max_i32(list: &[i32]) -> i32 { ... }

// A version for `f64`
fn find_max_f64(list: &[f64]) -> f64 { ... }
```

6. **Removing Tuples**: Tuples are removed in favor of ad-hoc monomorphic declarations. 
   1. `let person = (25, "John Doe")` => Uses generic polymorphic tuple to hold data of different types, being less explicit about the type of data being held
   2. If that tuple is converted to a struct, we know the type of each field of the struct.
   ```C
    typedef struct {
        int age;
        char* name;
    } Person;

    Person person;
    person.age = 25;
    person.name = "John Doe";
   ```
7. Removing dummy matches on boolean and units (TBC)
8. **Converting some F* constructs to C constructs**
   1. Inductives with only Constant Constructors become C enums [2] (<Research more about Inductive Types in Functional Programming>) (TBC)
   2. Other inductives become C tagged unions [2]
   3. Pattern matches become switches or a series of cascading if-then-elses [2]
9.  **Transformation from a Functional to a Statement Language:** 
    1.  Global names converted to valid C identifiers
    2.  Expands top level definitions
    3.  All expressions that are not C expressions are converted to statement 
10. At this point, the program fits the definition of Low*
11. **KaRaMel converts the Low\* program to C\* (TBC)**
    1.  Goes from a lexical scope to block scope (<Research more about lexical vs block scopes>)
    2.  Optimises functions that return unit into functions that return void
    3.  Optimises functions that take unit into functions that take no parameters
12. **C\* Program converted to an abstract C (TBC)**
    1.  Turning ML-style types into specifiers and declarators
    2.  Replacing all high-level nodes with actual C constructs
    3.  Making the initialization of buffers explicit
13. **Prints the C abstract tree into actual syntax (TBC)**
    1.  Respecting the Precedence of Operators
    2.  Introducing Sensible Indentation
    3.  Dealing with C abmiguities

# Questions to ask Matt:
- Deep vs Shallow Embedding
  - Write special functions for Kiama, carefully constructed so it does not feel like you are using a library (Shallow)
    - Instead of having to "string". ~> (params)
    - We can just do "string" ~> "foo"
    - Embedding a language just with a library 
  - Deep: .process() -> does its own little compilation, parse, execute, interprete
- Inductive types in Functional Programming
- Lexical vs Block scope 

# Questions for Amos:
1. KaRaMel starts with the ML-like AST, but it doesn't mention what happens to the original F*/Pipit code before we have the `ML-like AST`
  - There is info on how Low* gets converted to ML-like AST using F*'s existing normalizer and eraser facility, which then gets fed into an input to KaRaMel
  - BUT, in the KaRaMel documentation which covers the compilation of F* into C, the ML-like AST gets converted to Low* before being converted to C*, then C
  - So how does the Flow actually go?
    - `F*/Pipit ->(via F*'s erasure/normaliser facility) ML-like AST -> (Using KaRaMel) Low*/λow∗(?) -> C* -> C` [2] [3] [5]
      - λow∗ is the core of Low*, post erasure [2]
      - Pipit is considered "above" Low*, Low* is being treated as one of the intermediary steps to C
2. But we also have
    - `Low* -> (via F*'s erasure/normaliser facility) ML-Like AST -> (Using KaRaMel) -> λow∗ -> C* -> C` [2]
3. F* can be compiled to OCaml via `--codegen `OCaml`, and OCaml can be converted to C. So why is KaRaMel being used? What is the difference between the two ways?
  - Is the `ML-like AST` basically the OCaml code F* is converted to before being fed to KaRaMel?
  - OCaml is needed to use KaRaMel

# References:
- [1] Proof-Oriented Programming in F*, Page 11 Section 1.5, Page 88 Section 10.3, Nikhil Swamy, Guido Martínez, and Aseem Rastogi
- [2] Verified Low-Level Programming Embedded in F∗, Page 3 Fig 1, Section 4.1, JONATHAN PROTZENKO, JEAN-KARIM ZINZINDOHOUÉ
- [3] KaRaMel https://github.com/FStarLang/karamel
- [4] https://rustc-dev-guide.rust-lang.org/backend/monomorph.html
- [5] Pipit on the Post: Proving Pre- and Post-conditions of Reactive Systems, Section 5