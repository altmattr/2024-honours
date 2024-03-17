# heading How does Processing 4 get coverted into Java?

### You can only write bare processing code in the processing editor...
*Unless you write your own translater of course!*
When writing processing in a .java file, you must include the library and reformat your code how the PDE Editor would for yourself. To re-format your processing code into java, the PDE utilises ANTLR, a parser generator for translating code:

- JavaLexer.g4 is the basic grammer for java
- JavaParser.g4 is the basic parser for java
- Processing.g4 is the grammer for processing

When ran using these files, ANTLR generates files such as **ProcessingBaseListener** which is the basic layout for the listener(the thing that does the actual work). 

The interesting files for us are:

- PdeParseTreeListener.java
- PdePreprocessor.java
- Sketch.java
- SketchCode.java
- JavaBuild.java
- Compiler.java

Other Files 

### Sketch.java
**Sketch.java** encaptulates the current sketch *(go figure)*. A sketch is made up of multiple SketchCodes or **tabs**. It also has helperfunctions, ect...

### SketchCode.java
**SketchCode.java** handles a singular tab. It keeps track of its data, file name, helper functions to edit/load the file, ect...

### JavaBuild.java
**JavaBuild.java** is responsible for calling the **PdePreprocessor.java** and **Compiler.java**.

### PdePreprocessor.java
Processes the parse tree via **PDEParseTreeListener.java** //this might be wrong, please investigate...

### PdeParseTreeListener.java
**PdeParsetreeListener.java**

---
**sidenote:** This is how it is suggested to edit the editor directly within the CONTRIBUTING.md. They otherwise suggest adding new functionality to processing via a library. 

> With that in mind, any work on updating the editor and adding new features should be focused on further [adapting the preprocessor and compiler](https://github.com/processing/processing4/issues/117) to be wrapped using the [Language Server Protocol](https://en.wikipedia.org/wiki/Language_Server_Protocol), so that we can link to other existing editors (Visual Studio Code and many others). It should be possible to create a Java-only, headless implementation that wraps the current source in this repository and can communicate via LSP.
---
