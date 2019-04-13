# Lesson 3

## Introducing Functions

Commonly programs carry out the same or similar tasks repeatedly during the course of their execution. For you to avoid rewriting the same piece of code over and over again, Javascript has the means to parcel up parts of your code into reusable units, called *functons*. Once you have written a function, it is available for the rest of your program to use, as if it were itself a part of Javascript language.

Using functions also make your code easier to debug and maintain. Suppose you have written an application to calculate shipping costs; when the tax rates or haulage prices change, you'll need to make changes to your script. There may be 50 places in your code where such calculations are carried out. When you attempt to change every calculation, you are likely to miss some instances or introduce errors. However, if all such calculations are wrapped up in a few functions used throughout the application, then you just need to make changes to those functions. Your changes will automatically be applied throughout the application.

Functions are one of the most basic building blocks of Javascript and will appear at virtually every script you write.

## General Syntax

Creating a function is similar to creating a new Javascript command that you can use in your script. Here is the basic syntax for creating a function:
```javascript
function sayHello() {
  alert("Hello");
  // .. more statements go here ..
}
```
You begin with the keyword *function* followed by your chosen function name with parentheses appended, then a pair of curly braces {}. 
Inside the braces go the Javascript statements that make up the function. The preceding example, simply has one line of code to pop up an alert dialog, but you can add as many lines of code as necessary.

> Caution
### Take Care with Case
the keyword *function* must always be used in lowercase; otherwise, an error will be generated.

----

To keep things tidy, you can collect together as many functions as you like into one <script> element:
```html
<script>
  function doThis() {
    alert("Doing this");
  }
  function doThat() {
    alert("Doing that");
  }
</script>
```

## Calling Functions

Code wrapped in a function definition will not be executed when the page loads. Instead, it waits quietly until the function is called.

To call a function, or to invoke a function, you simply use the function name, with parentheses, whenever you want to execute the statements contained in the function.
```javascript
sayHello();
```

For example, you may want to add a call to your new function *sayHello()* to your *onClick* event of a button:
```html
<input type="button" value="Say Hello" onclick="sayHello()" />
```

> Tip
### Function Names
Function names, like variable names are case sensitive. A function called *myFunc()* is different to *myfunc()*. Also, it is really helpful to the readability of your code to choose meaningful function names.

----

> Tip
### About Methods
You have already seen examples of using *methods* associated with Javascript objects, such as *document.write()* and *window.alert*.
Methods are simply functions that belong to a specific object.

----

## Putting Javascript Code in the Page *<*head*>*

Upto now, all our Javascript code examples were placed in the <body> part of HTML page. Using functions lets you employ the much more common, and usually preferable, practice of storing your Javascript code in the <head> of the page. Functions contained within a <script> element in the page head, or in an external file included via the *src* attribute of a <script> element in the page head, are available to be called anywhere on the page. Putting functions in the document's head section ensures that they have been defined prior to any attempt being made to execute them.

> Caution
### Multiple Definitions
Ensure your Javascript functions are not defined more than once. This can sometimes happen when you include more than one sccript element in a page, especially where one or more of these references an external file of Javascript commands.
If you call a function that has been defined multiple times, Javascript won't issue an error message. It will simply use the latest definition of the function, so these can be difficult bugs to find!

----
Look at Functions_in_the_Page_Head.html example to see a function defined in the head section of an HTML page.
From the page you see is the function definition has been placed inside a <script> element in the page head, but the call function has been made in a different place entirely - on this occasion, from the *onClick* event handler of a button in the body section of the page.
The result of clicking the button is an alert dialog with the text "Hello".

## Passing Arguments to Functions

It would be rather limiting if your functions could only behave in an identical fashion each and every time they were called, as would be the case in the preceding example.

Fortunately, you can extend the capabilities of functions by passing data to them. You can do this when the function is called, by passing it one or more arguments.
```javascript
functionName(arguments);
```
Let's create a simple function to calculate the cube of a number and display the result.
```javascript
function cube(x) {
  alert(x * x * x);
}
```
Now you can call the function by replacing x with a number. Calling the function as in the following line results in a dialog being displayed containing the results of the calculation, in this instance 27:
```javascript
cube(3); // Answer is 27.
```
Ofcourse, you could easily pass a *variable name* as an argument. The following code would also generate a dialog containing the number 27:
```javascript
var length = 3; // Variable name "length"
cube(length); // Calling the function with argument being the variable name "length"
```

> Note
### What is in a Name?
You will sometimes hear or see the word *parameters* used in place of argument, but it means the same thing. *Parameters* are the values the function expects, and are baked into function definitions from the start, whereas *arguments* are the valyes provided for those parameters when the function is called. The two are used interchangebly by programmers.

----

## Multiple Arguments

Functions are not limited to a single argument.
