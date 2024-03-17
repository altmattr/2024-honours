# Overview: 
- Safety critical control systems are implemented uysing Lustre/Scade
- Model Checkerse like Kind2 are used to check whether the implementation satisfies the high level requirements 
- It is critical to prove such programs corrected, AND ensure that the proved properties apply to the compiled code 
- The high level code written in Lustre/Scade is compiled to C code to run on a microcontroller

## Problems with Using Lustre/Scade
### 1. Semantic Mismatch
The semantic mismatch issue arises when there's a discrepancy between the `behavior assumed or verified at the high-level model` and the `actual behavior of the compiled code running on hardware`. 
1. Model checker semantics does not match the compiled code semantics
2. Hence, properties proved at high level implementation doe not hold for the compiled code running on actual hardware/real life systems 
3. So, compiler and model checker should share the same semantics 
### 2. Lack of suficient manual proofs when automated proofs fail
1. Model checkers do not provide many options for manual proofs when the automated proof techniques fail

## How does using Pipit Solve these problems 
Pipit is an embedded language in F*, used for both the implementation and verification of safety critical control systems 
### 1. Using a single unified framework
1. All of the following things are done using a s**ingle unified framework**, the F* family (F*, Pipit, Low*)
   1. ***Implementation of these control systems by writing high level code*** : Done using `Pipit`
   2. ***Verification of the high level code*** : Done using `F*s verification capabilities`
   3. ***Microcontroller code generation*** : Done using `Low* (a subset of F*)`, which can be compiled to effecient C code
2. **Translation to Transition System:**
   1. Pipit translates its high level expressions to a transition system 
      1. This transition system can be proven using `k-inductive proofs`, which is a form of model checking 
         1. Helps prove properties of all possible states of the system
      2. This transition system is `verified to be an abstraction of the original semantics`
         1. **Inference**: So proved properties of the transition system should apply to both the High level Pipit code, and the compiled code in C (To check with Matt)
3. **Microcontroller Code generation with Low\***
   1. Pipit/F* is converted to Low*, which is translated to effecient C code while preserving the original F*/Pipit specifications. To execute programs, Pipit can generate executable code, which is total and semantics-preserving [1]
      1. **Inference**: The C code generated from Low* should have the same semantics as the high level specification written using Pipit, addressing the potential semantic mismatch issue (To check with Matt)
         1. **Assumption**: Pipit has taken over the role of a model checker like "Kind2", so Pipit semantics matching the compiled C code semantics has the same implications as `model checker and compiled code sharing the same semantics` (To check with Matt)
4. **Allowing both automated and manual proofs**
   1. By using F*'s proof utomation and manual proof capabilities to verify controllers


# References:
- [1] Pipit on the Post: Proving Pre- and Post-conditions of Reactive Systems, Section 1