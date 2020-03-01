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

## GETTING A SINGLE VALUE OUT OF A FUNCTION
 Some funciton return information to the code that called them. For example, when perform a calculation, they return the result.
 
 ~~~js
 function calculateArea(weidth, height){
 var area = weidth*height;
 return area;
 }
 var wallOne = calculateArea(3, 5);
 
 var wallTwo = calculateArea(8, 5);
 ~~~
 
## GETTING MULTIPLE VALUES OUT OF A FUNCTION 
Functions can return more than one value using an array.
For example, this function calculates the area and volume of a box. 

~~~js
function getSize (width, height, depth) {
var area = width * height;
var volume = width * height * depth;
var sizes= [area , volume];
return sizes;
}
var areaOne = getSize (3, 2, 3)[0];
var volumeOne = getSize (3, 2, 3)[1];
~~~

## What is an object 

Objects group together a set of variables and functions to create a model 
of a something you would recognize from the real world. In an object, 
variables and functions take on new names. 

-------------------------------------------------

**Programmers use a lot of name/value pairs:** 

* HTML uses attribute names and values. 
* CSS uses property names and values. 

**In JavaScript:**

* Variables have a name and you can assign them a 
value of a string, number, or Boolean. 
* Arrays have a name and a group of values. (Each 
item in an array is a name/value pair because it 
has an index number and a value.) 
* Named functions have a name and value that is a 
set of statements to run if the function is called. 
* Objects consist of a set of name/value pairs 
(but the names are referred to as keys). 

## WHAT IS A DOCUMENT OBJECT MODEL   

Html tags come together to form document object model.
We can manipulate our elements with javascript on this document

## Veri Seçimleri 

### Element ID'e Göre Seçme
~~~js

let element;

element = document.getElementById("todo-form");
element = document.getElementById("task-title");

~~~

### Element Class'a Göre Seçme 
> Bir class'tan birden fazla olacaktır bundan dolayı eğer sadece bir veriyi seçmek istersek onun indexsini girmemiz lazım 
        
~~~js
let element: 

element = document.getElementByClassName("list-group-item");
element = document.getElementByClassName("card-header")[3];

~~~
### Element Tag'e Göre Seçme

~~~js
let element: 

element = document.getElementByTagName("div");

~~~

### Query Selector - Css Selector - Tek Bir Element

~~~js
let element;

element = document.querySelector("#todo-form");
element = document.querySelector("#tasks-title");

element = document.querySelector(".list-gruop-item");

element = document.QuerySelector("li");
element = document.QuerySelector("div");
~~~

### QuerySelectorAll - Tüm Elementleri Seç

~~~js

let element;

element = document.querySelectorAll(".list-gruop-item")  //  Node list

element.forEach(function(el){
      console.log(el);
})

~~~

## Element Attribute

~~~js 
console element = document.querySelector("#clear-todos");

console.log(element.id);           // we can learn ID of element
console.log(element.ClassName);    // To print class name 
console.log(element.ClassList);    // we can print Class list, what the have in the class 
console.log(element.classList[1]); // what you want to learn for which index
console.log(element.textContent);  // shows only text data 
console.log(element.innerHTML);    // show all html tag's and data
console.log(element.href);         // shows the link in
console.log(element.style);        // we can see css attribute and add css attribute

~~~

### Changing Stayle and Element Attribute

~~~js
console element = document.querySelector("#clear-todos");

element.classNAme = "btn btn-success";   // Adding a new stayle to button
element.stayle.color = "#000";           // Adding new color 
element.styale.marginLeft = "20px"       // Adding margin to left
element.href = "https://www.google.com/" // New link added 
element.taget = "_blank";       
                                        
                                        //And more
~~~




