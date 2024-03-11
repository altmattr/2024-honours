From my inital poke at the processing 4 and processing 5.js repos, implementing pattern matching may be more similar than we originally thought.
On the java side, it seams that most of their code is manipulating the java.awt package, obsfuscating some of the complexity from the user.
Implementing pattern matching into p4 looks like it will be creating a class PMatch (to fit the rest of their standards) to deal with the pattern matching, and placing it in processing4/core/src/processing/core. either that, or modifying PApplet and creating a method, or both.

The way processing 5.js works is rather different than processing 4. Some method names are changed to something that makes more sense in the new context, like how size is changed to createCanvas, "because you can think of your sketch as more than just the drawing canvas"(from processing transition in p5.js repo). Instead of manipulating awt, 5.js is web based(go figure). It is my understanding that processing5.js is in layers like a cake:

html:           provides the basis of the website, defines the layout of the page.
CSS:            makes those ui objects pretty.
javascript:     adds functionality to those ui objects.
processing5.js: a library that adds functionality similar to processing4.

regardless of how things are rendered to the screen, 