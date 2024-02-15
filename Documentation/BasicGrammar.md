# Basic Grammer

So this is where all the basic rules and syntax will be laid out, no methods, nothing extra, that will be in a separate markdown file
#
```
//Nade will use the same comment syntax as Java, because I think it looks nice

// <- so this is a line comment
/* <- and this is a in-line comment -> */

// Nade will also use the same end line syntax as Java/C#, again because I like the way it looks

// defining methods will be split up into multiple parts, the method define, the method logic, and anything else I come up with on the fly as I am writing this

// the basic "parent" method, looks like this:
method define:(/*method name goes here*/)
// to declare parameters in the method, you do:
method define:(/*method name*/{param.type./*parameter type here*/})
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

// parentheses act like curly braces in Java or C#, they encapsulate anything relating to the body header (i.e. method define:(), method logic:()(), define return:(), etc.)

//NOTE: Variables can be defined outside of methods and datatypes, mirroring Java and C#.
```
That is the basic "structure" of methods, I will now go into the variations of method header definitions and how to define and call methods:
```
// methods, similiarly to Java and C#, have 3 types: private, public, and protected
// private can only be called from the parent body or a child body
// public can be called anywhere by anything
// protected can be called from only the parent body, so if I have a method, lets say "make triangle", and it is protected, only the body it is written in, lets say "Draw", can define it

// to define a method as one of these, you write its method define like:
method define:(Protected)(make triangle)
//NOTE: Protected, Private, and Public are the ways you need to define them, writing them in lower-case will throw an error
// excluding the method type will default the method to Public

// method names are... going to be confusing, think of them as strings, they can have anything in them, but to be called correctly, they need to be EXACT, so if you have a method named "make Triangle", to define it, you need to do exactly "make Triangle".
// "maketriangle", "make triangle", etc. WILL NOT WORK

// to define a method name, you need to do:
method define:(/*insert method name here*/)

// An example method name is:
method define:(write Hello World)

// for method parameters, make sure to surround your parameter in curly braces, like:
method define:(write {param.type.string})

// to define a name to a parameter, write the parameter declaration like:
// {param.type.string : <parameter name>}
// this will look like this in a full method declaration:
method define:(add{param.type.int : a}{param.type.int : b})
//NOTE: white-space is not required inside the parameter declarations, I put that there for readability

//NOTE: for custom data types, use the body path of it
// Ex: <bodyname>.<datatypename> or <packagename>.<bodyname>.<datatypename>, etc.

// to call a method, you need to use:
method call:(/*method name plus parameters*/);

// if you are setting the return value to a variable, do:
method call:(/*method name plus parameters*/);
/*variable type (if not defined yet)*/ /*variable name*/ = (/*method name plus parameters*/) : method return;

// an example would be:
int sideLength = (getSideLengthOf{square}) : method return;

// if the variable type has already been defined:
int sideLength; // define the variable and its type
sideLength = (getSideLengthOf{square}) : method return; //NOTE: you do not need to have white space in this line of code, I do that to make it easier to read.
```
This is how you define a custom datatype in Nade:
```
datatype define: (/* datatype name here, think of this like class names for Java */)
datatype init: (/* datatype name here*/)(/* this is like the constructors in Java */) //NOTE: Excluding datatype init:() will use the default empty constructor
datatype logic: (/* this is where you would put all of your variables, methods, etc. */)
//NOTE: Datatypes cannot be defined inside of a method, only in a body, they cannot be defined outside of a body either
```
This is how you would define a body, as well as the various relevant information regarding constructing a body:
```
// to define a body, which is like a class in Java, you do this:
body define: (/* body name here, again think Java class names */)(/* this set of paraentheses holds all your datatypes, logic, methods, etc., etc. */)

// bodies, just like methods, have specific types to them
// bodies have two sets of types: 
// abstract, system, normal/default
// and private, public, protected

// abstract is a body that can't have datatypes, but can have methods
// system is a body that does have datatypes, but cannot have methods
// normal/default is a body that can have datatypes and methods
// all of these types can be offspring or parents

// private can only be accessed by a parent or offspring
// public can be accessed by anything, anywhere
// protected can only be accessed by anything in its package

//NOTE: packages are just groupings that only affect the accesibility permissions of methods and bodies

// to define a body with these types you do:
body define: (/*if you are defining a abstract body or a system, you would write it here*/)(/* public/private/protected */)(/* body name */)(/* and where all the methods/datatypes/logic/etc go */)

// body logic is the bodies "Update" method, think Unity's Update() method
// an example:
body define: (Public)(TestBody)(

    Public int count; // automatically defaults to 0

    method define: (countUp)
    method logic: (countUp)(
        define return: ({data.type.null};);
        count++; // adds 1 to count
        method call: (write {count});
        return: (null;);
    )

    body logic:(
        method call: (countUp); // counts up until the program is stopped
    )
)

// body init is the bodies "main" method, think Java's main, you all know it, "public static void main(String [] args){}", basically "body init: ()" is Nade's version of that
// an example
body define: (Public)(TestBodyInit)(
    body init:(
        method call: (write {"Hello World!"});
    )
)

```
