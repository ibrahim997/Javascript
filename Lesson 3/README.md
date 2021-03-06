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

Functions are not limited to a single argument. When you want to send multiple arguments to a function, all you need to do is separate them with commas:
```javascript
function times(a, b) {
  alert(a * b);
}
times(3, 4); // alertst '12'
```
You can use as many arguments as you need.

> Caution
### Count Your Arguments
Make sure your function calls contan enough argument values to match the parameters specified in the function definition. If any of the parameters in the definition are left without a value, Javascript may issue an error, or the function may perform incorrectly. If your function call is issued with too many arguments, Javascript will ignore the extra ones.

----

It's important to note that the names given to parameteres in the definition of your function have nothing to do with the names of any variables whose values are passed to the function.The variable names in the argument list act like placeholders for the actual values that will be passed when the function is called. The names that you give to arguments are only used inside the function definition to specify how it works.

## Try It Yourself

### A Function to Output User Messages
This exercise is about a function that can send te user a message about which button the user has clicked on. You place the function definition in the <head> section of the page and call it with multiple arguments.

Here is the function:
```javascript
  function buttonReport(buttonId, buttonName, buttonValue) {
      // Information about the id of the button
      var userMessage1 = "Button id: " + buttonId + "\n";
      // Information about the button name
      var userMessage2 = "Button name: " + buttonName + "\n";
      // Information about the button value
      var userMessage3 = "Button value: " + buttonValue;
      // Alert the User
      alert(userMessage1 + userMessage2 + userMessage3);
  }
  ```
The function *buttonReport* takes three arguments, those being the id, name and value of the button element that has been clicked on. With each of these three pieces of information, a short message is constructed. These three messages are then concatenated into a single string which is passed to the *alert()* method to pop open a dialog containing the information.

> Tip
### Special Characters
You may have noticed the first two string have the element "\n" appended to the string; this is a **new line character**, forcing the message within the alert dialog to return to the left and begin a new line. Certain special characters like this one must be prefixed with "\" if they are to be correctly interpreted when they appear in the string. Such a prefixed character is known as an escape sequence.

----

To call the function, you put a button element on the HTML page, with its id, name and value defined:
```html
<input type="button" id="id1" name="Button 1" value="Something" />
```

You need to add an *onClick* event handler to this button from which to call the function. Here, you can use the *this* keyword as discussed in Lesson 2.

The complete exmaple is shown in the file called "A_Function_To_Output_User_Messages.html".

## Returning Values from Functions

How can you get information back from your functions? To achieve this, you can use a mechanism to collect data from a function call - the *return value*.
Let's see how it works using a modified version of the *cube()* function:
```javascript
function cube(x) {
  return x * x * x;
}
```
Instead of using an *alert()* dialog within the function, as in the previous example, this time the required result is prefixed with the *return* keyword. To access this value from outstide the function, you simply assign to a variable the value returned by the function:
```javascript
var answer = cube(3);
```
After this line is executed, the variable *answer* will have the value 27.

Remeber to call a function, you must add the parentheses to the function name as in the preceding example. If you use the function name without the parentheses, Javascript will assume you are referring to the definition of the function, rather than the valye it returns. Suppose that in the preceding code snippet, you had instead used:
```javascript
var answer = cube;
```
When this line is executed, instead of the number 27, the varibale answer will contain an identical function definition to that of cube(), so the following line, when executed, would alert a value of 27:
```javascript
alert(answer(3)); // Alerts 27
```

> Note
### Data Types of Return Values
The vales returned by functions are not restricted to numerical quantities as in this example. In fact, functions can return values having any of the data types supported by Javascript. If no return statement is included in a function, it will by default return a value of *undefined*.

----

> Tip
### Passing Return Values to Other Statements
Where a function returns a value, you can use the function call to pass the reeturn value directly to another statement in the code. For example, instead of:
```javascript
var answer = cube(3);
alert(answer);
```
you simply use:
```javascript
alert(cube(3));
```
The value of 27 returned from the functon call *cube(3)* immediately becomes the argument passed to the *alert()* method.

----

## Anonymous Functions

There is a more convenient and elegant way to define a function, without having to create a separate named function and then later assign assign it by name to the required method.

In a previous example, you used this line of code:
```html
<input type="button" value="Say Hello" onclick="sayHello()" />
```
You'll recall that this was the function definition:
```javascript
function sayHello() {
  alert("Hello");
}
```
An alternative way to achieve the same effect would be like this:
```javascript
var sayHello = function () { alert("Hello"); };
```
Because you have not needed to give a name to your function prior to assigning it, this technique is referred to as using an anonymous function. This way of defining functions is concise and useful and will see more in the lessons to come.

## Summary

In this lesson you learnt about what functions are and how to create them in Javascript. You learned how to call functions from within your code and pass information to those functions in the form of arguments. You also learnt how to return information from a function to its calling statement. And finally anonymous functions.

## Exercise

Write a function to take a temperature value in Celsius as an argument and return the equivalent temperature in Fahrenheit, basing on the code from Lesson 2.
Test your function in an HTML page having three buttons that, when clicked, pass values of 10, 20 and 30 degrees Celsius, respectively, to the function.

