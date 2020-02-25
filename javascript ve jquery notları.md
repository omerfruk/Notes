# javascript ve jquery notları

We will look at what the code on the right does
shortly, but for the moment note that:

- Each of the lines of code in gree n is a statement.
- The pink curly braces indicate the start and end of a code block. (Each code block could contain many more statements.)
- The cod e in purple determines which code should run (as you will see on p149).

```js
{
var today= new Date{);
var hourNow = today.getHours{) ;
var greeting;
if (hourNow > 18) {
greeting= 'Good evening';
}
else if (hourNow > 12) {
greeting= 'Good afternoon';
}
else if (hourNow > O) {
greeting 'Good morning';
}
else {
greeting 'Welcome';
}
document.write(greeting);
}
```

### JAVASCRIPT IS CASE SENSITIVE

JavaScript is case sensitive so hourNow means
something different to HourNow or HOURNOW.

## Comments

~~~js

/* This script displays a greeting to the user based upon the current time. 
It is an example from JavaScript & jQuer y book */

var today= new Date(); // Create a new date object
var hour Now = today.getHours(); //find the current hour
var greeting;

~~~

if you want to add comments in your code, you must be use (/\*multi-line comments*/ or //single-line commants )

## Variables

The use of variables to represent numbers or oth er
kinds of data is very similar to the concep t of algebra
(where letters are used to represent numbers).

**Variables :** How to declare them

~~~js
var quantity;
~~~

**var :** Variable Keyword

> The JavaScript interpreter knows that this keyword is used to create a variables

**quantity :** Variable Name 

**Variavles :** How to assign them a value

~~~js

quantity = 3;

~~~

**quantity :** Variable Name

**= :** Assignment Operator

**3 :** Variable Value

## Function 

To create a **function** you give it a name and then write statemants needed the achieve its task inside the curly braces 


~~~js
 
function sayHeloo() {
    document.write("Hello");
}

~~~

##### function : function keyword

##### sayHeloo() : function name 

~~~js
  document.write("Hello");
~~~

Code block (in curly braces)

### calling a function

To run the code in the function, you use the function name followed 
By parentheses

~~~js
SayHello();

~~~

### Declaring function that need information 

Sometimes a function need specific information the perform its tesk. In such cases, when you declare the function you give it 
Parametres. Inside the function, the parametres act like variable. 


~~~js
function getArea(width,height){
    return width×height;
}
~~~

