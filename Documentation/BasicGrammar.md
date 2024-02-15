# Basic Grammer

So this is where all the basic rules and syntax will be laid out, no methods, nothing extra, that will be in a separate markdown file
#
```
//Nade will use the same comment syntax as Java, because I think it looks nice

// <- so this is a line comment
/* <- and this is a in-line comment -> */

// Nade will also use the same end line syntax as Java/C#, again because I like the way it looks

// defining methods will be split up into multiple parts, the method call, the method logic, and anything else I come up with on the fly as I am writing this

// the basic "parent" method, looks like this:
method call:(/*method name goes here*/)
// to declare parameters in the method, you do:
method call:(/*method name*/{param.type./*parameter type here*/})
//NOTE: Parameters can be ANYWHERE inside the method name, you don't need them in a specific area inside the method name like the beginning or end

// to declare the method logic:
method logic:(/*you can declare the method name, but that is optional*/)
(
    define return: ({data.type./*return type here*/};);
    //NOTE: You can return multiple return types, that is why you need to place a semi-colon on the inside of the return definition as well as at the end of the line
    //define return needs to be AT THE BEGINNING of your method
    //defining return is required!

    //to define that the method returns nothing:
    // define return: ({data.type.null};);

    // method logic goes here

    // return your data:
    return:(/*insert variable(s) of correct type(s)*/;);
    // if you are returning nothing:
    return:(null;);
)

// parentheses act like curly braces in Java or C#, they encapsulate anything relating to the body header (i.e. method call:(), method logic:()(), define return:(), etc.)
```
That is the basic "structure" of methods, I will now go into the variations of method header definitions and how to call methods:
```
// methods, similiarly to Java and C#, have 3 types: private, public, and protected
// private can only be called from the parent body or a child body
// public can be called anywhere by anything
// protected can be called from only the parent body, so if I have a method, lets say "make triangle", and it is protected, only the body it is written in, lets say "Draw", can call it

// to define a method as one of these, you write its method call like:
method call:(Protected)(make triangle)
//NOTE: Protected, Private, and Public are the ways you need to define them, writing them in lower-case will throw an error
// excluding the method type will default the method to Public

// method names are... going to be confusing, think of them as strings, they can have anything in them, but to be called correctly, they need to be EXACT, so if you have a method named "make Triangle", to call it, you need to do exactly "make Triangle". "maketriangle", "make triangle", etc. WILL NOT WORK

// to define a method name, you need to do:
method call:(/*insert method name here*/)

// An example method name is:
method call:(write Hello World)

// for method parameters, make sure to surround your parameter in curly braces, like:
method call:(write {param.type.string})

//NOTE: for custom data types, use the body path of it
// Ex: body1.datatype or package.body1.datatype, etc.
