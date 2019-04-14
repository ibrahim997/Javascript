## Lesson 4

## Scope of Varibales

You have already seen how to declare variables with the *var* keyword. There is a golden rule to remember when using functions:
"Variables declared inside a function using the keyword *var* exst only inside that function."

This limitation is known as the *scope* of the varibale. Let's look at an example:
```javascript
// Define our function addTax()
function addTax(subtotal, taxRate) {
  var total = subtotal * (1 + (taxRate/100) );
  return total;
}
// Now let's call the function
var invoiceValue = addTax(50, 10);

alert(invoiceValue); // Works correctly
alerrt(total); // Works incorrectly
```
If you run this code, you first see an *alert()* dialog with the value of the variable *invoiceValue*. You do not however, see the dialog containing the value of the variable total. Instead Javascript simply produces an error. Whether you see this error reported depends on your browser settings. Javascript is unable to display an *alert()* dialog with the value of your variable total.

The reason is that the declaration of the variable total is placed inside the instruction block that forms the definition of the *addTax()* function. Outside the function the variable total simply does not exist (or as Javascript puts it, it is "undefined"). The *return* keyword passes back just the value stored in the variable *total*, and that value is then stored in another variable, *invoiceValue*.

We refer the variables declared inside a function definition as being *local variables*, that is local to that function. Variables declared outside any functio are known as *global variables*. Gloabl and local variables can have the same name but still be different variables.

The range of situatiosn in which a variable is defined is known as the *scope* of the variable - you can refer to a variable having a local scope or a gloabl scope.

## Try It Yourself

### Demonstrating the Scope of Varibales

To illustrate the issue of a variable's scope, let's look at the following piece of code:
```javascript
var a = 10; var b = 10;
function showVars() {
    var a = 20; // Declare a new local variable 'a'
    b = 20; // Change the value of global variable 'b'
    return "Local variable 'a'' = " + a + "\nGlobal variable 'b' = " + b; 
}
var message = showVars();
alert(message + "\nGlobal variable 'a' = " + a);
```
Within the *showVars()* function, two variables, *a* and *b* are manipulated. The varibale *a* is defined inside the function; this is a local variable that exists only inside the function, quite separate from the global variable *a* that is declared outside the function or at the beginning of the script.

The variable *b* is not declared inside the function, but oustide; it is a *global* variable.

The "Demonstrating_the_Scope_of_Variables.html shows the preceding code with an HTML page.

When the page is laoded, *showVars()* returns a message string containing information about the updated values of the two variables *a* and *b*, as they exist inside the function - *a* with local scope and *b* with global scope.

A message about the current value of the other global variable, *a*, is then appended to the message, and the message displayed to the user.

## Using the *this* keyword

You may recall using such a keyword in Lesson 2, while you were defining an inline event handler:
```html
<img src="tick.gif" alt="tick" onmouseover="this.src='tick2.gif';" />
```
When used in that way, *this* refers to the HTML element itself - in the preceding example the <img> element.

When you use the *this* keyword inside a function, the keyword *this* refers to whatever "owns" the function - something we refer to as the *patent scope* of the function.

In the "Try It Yourself" above example, the *showVars()* function was created at the "top level". In other words, it belongs to the global object (the object that also owns any variables that are in global scope). In a web browser, the global object is normally the browser's *window* object.

So what would happen if you asked the function to return the value of *this.a*, as in the following code snippet?
```javascript
function showVars() {
  var a = 20;
  var b = 20;
  return "this.a = " + this.a + "\nLocal variable 'a' = " + a + "\nGlobal variable 'b' = " + b;
}

var message = showVars();
alert(message + "\nGlobal variable 'a' = " + a);
```
Since *this* refers to the global object, *this.a* refers to the variable *a*, which is in the global scope.

## Declaring Variables Using *let*

Until recently, Javascript had only two types of scope - namely, the *function* scope and the *global* scope.

Having only these two types was a nuisance to many programmers, especially those who are more familiar with other languages. Many other programming languages allow variables to have so-called block scope (a block in Javascript constitutes the entire contents of a pair of curly braces {}). A variable with block scope would be accessible only to a program statement occuring within the same block as the variable definition.

Recent updates to the Javascript language have seen this omission corrected with a new keyword *let*, which allows you to define a variable with exactly this block scope.

Now look at the following code snippet. Suffice to say that such a statemnt allows your program to execute a block of statements only if a particular condition is met.
```javascript
function myFunction(x) {
  var y = x;
  if (x > 50) {
    var y = 10;
    alert("Inner y = " + y); // Alert 10
  }
  alert("Outer y = " + y); // Alert 10
  .. more statements ..
}
```
What will the program display in the alert dialog, if we call the function with an argument of 100? The valye of y will initially be set to 100, with *function scope*; that is, its value will be accessible anywhere within the function.

Since the value of x is greater than 50, the inner block of code will be executed. The first command within that inner block will redeclare y, and since the *var* keyword gives the declared variable function scope, the new value will be accessible throughout the entire function.
The result is that, when you leave the inner code block and the second alert is executed, the new value of y (that is, a value of 10) will be displayed. Any further lines of code in the outer block will "see" this new value of y.

Now consider what happens when *let* is used instead in the inner block:
```javascript
function myFunction(x) {
  var y = x;
  if (x > 50) {
    let y = 10;
    alert("Inner y = " + y); // Alert 10
  }
  alert("Outer y = " + y); // Alert 100
  .. more statements ..  
}
```
Here the variable y declred within the inner code block has only *block scope*; when execution leaves the inner block and performs the second alert, a value of 100 will be reported for y and seen by any subsequent lines of code in the outer block.

## Declaring Constants with the *const* Keyword

Sometimes you need to store a value that simply can't be changed by later code. Examples might include, for instance, the initial setup parameteres of your program, such as the width and the height of a page element for displaying output.

You can achieve this result by using the keyword *const*. A *const* declaration creates a *constant* - a value that can't be changed by reassignment later in the code. Any attempt to change the value of a variable declared using *const* will result in an error:
```javascript
function myFunction() {
  const x = 300;
  x = 400; // An error is generated at this line of code
  
  ... more statements ...
}
```

## Try It Yourself

### Checking Out const

Let's look at how *const* operates. We will be using Google Chrome for this exercse.

Instead of writing code in a text file, open the Javascript Console for your browser. In this case of Chrome you can do that by pressing CTRL+SHIFT+J.

These are the steps to take and write down each result from the tasks in each step below:
1. Define a constant using the *const* keyword and choose a numeric value. Note: The console will issue *undefined* because the declaration of *const* does not return a value. For example: const MYCONST = 10
2. Try to redefine the value of the constant. For example: MYCONST = 11
3. Try to reassign a new value to the constant. For example: var MYCONST = 9
4. Try to reinitialise the constant with a new value. For example: const MYCONST = 20

All three attempts will lead Javascript to throw an error. Values declared using the *const* keyword canont be reinitialised, redeclared or reassigned.

## Arrow Functions

In the preceding lesson you learned about anonymous functions.
Here is an example used in that lesson:
```javascript
var sayHello = function() { alert("Hello"); };
```
A recent inclusion in Javascript is a more concise syntax for writing this sort of function, in which the arrow function (=>) is shorthand for anonymous function. These are generally known as *arrow* functions.
