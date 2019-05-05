## Lesson 5

## DOM Object and Built-in Objects

## Interacting with the User
Among the methods belonging to the *window* object, some are designed specifically to help your page communincate with the user by assisting with the input and output of information.

## *alert()*
You'll recall the *alert()* method would pop up an information dialog for the user. This modal dialog simply shows your message with a single OK button. The term *modal* means that script execution pauses, and all user interaction with the page is suspended until the user clears the dialog. The *alet()* method takes a message string as its argument.
```javascript
alert("This is a message");
```
*alert()* does not return a value.

## *confirm()*
The *confirm()* dialog is similar, in that it pops up a modal dialog with a message for the user. The *confirm()* dialog, though, provides a user with a choice; instead of a single OK button, the user may select between OK and Cancel. Clicking on either button clears the dialog and allows the calling script to continue, but the *confirm()* method returns a different value depeneding on which button was clicked - Boolean *true* in the case of OK, or *false* in the case of Cancel. Boolean values can only take one of the two values, *true* or *false*. 

The *confirm()* method is called in a similar way to *alert()*, passing the required message as an argument:
```javascript
var answer = confirm("Are you happy to continue");
```
Note that here, though, you pass the returned valye of *true* or *false* to a variable, so that you can later test the value and have the script take appropriate action depending on the result.

## *prompt()*
The *prompt()* method yet another way to open a modal dialog. In this case, the dialog, invites the user to enter information.
A *prompt()* dialog is called in just the same manner as *confirm()*:
```javascript
var answer = prompt("What is your full name");
```
The *prompt()* method allows for an optional second argument, giving a default response in case the user clicks OK without typing anything:
```javascript
var answer = prompt("What is your full name", "John Doe");
```
The return value from a *prompt()* dialog depends on what option the user takes:
* If the user types in input and clicks OK or presses Enter, the user input string is returned.
* If the user clicks OK or Enter, without typing anything into the prompt dialog, the method returns the default response (if any), as optionally specified in the second argument passed to *prompt()*.
* If the user dismisses the dialog (that is, clicking Cancel or pressing Escape), then the *prompt()* method returns *null*.

> Note
### The *null* Value
Javascript uses the *null* value on certain occassions to denote an empty value. When treated as a number, it takes the value 0; when used as a string, it evaluates to empty string (""); and when used in a Boolean value, it becomes *false*.

----

## Selecting Elements by Their ID
To select an element of your HTML page having a specific ID, all you need to do is call the document object's *getElementById()* method, specifying as an argument the ID of the required element. The method returns the DOM object corresponding to the page element with the specified ID.
Let's look at an example. Suppose your web page contains a *div* element.
```html
<div id="div1">
  ... Content of DIV element
</div>
```
In your Javascript code, you can access this *div* element using *getElementById()*, passing the required ID to the method as an argument.
```javascript
var myDiv = document.getElementById("div1");
```
You now have access to the chosen page element and all its properties and methods.

> Caution
### Make Surer There is an ID Value
The page element must have its ID attribute set. Because ID values of HTML page elements are required to be unique, the method should always return a single page element, provided a matching ID is found.

----

## The *innerHTML* Property
A handy property that exists for many DOM objects, *innerHTML* allows you to get or set the value of the HTML content inside a particular page element.
```html
<div id="div1">
  <p>Here is some original text"</p>
</div>
```
You can access the HTML content of the *div* element using a combination of *getElementById()* and *innerHTML*.
```javascript
var myDivContents = document.getElementById("div1").innerHTML;
```
The variable will now contain the string value:
```javascript
"<p>Here is some originl text</p>"
```
You can also use *innerHTML* to set the contents of a chosen element:
```javascript
document.getElementById("div1").innerHTML = "<p>Here is some new text instead!</p>";
```
Executing this code snippet will erase the previous HTML content of the *div* element and replaces it with the new string.

## Accessing Browser History
The browser's history is represented in Javascript by the *window.history* object, which is essentially a list of URLs previously visited. Its methods enable you to use the list, but not to manipulate URLs explicity.
The only property owned by the *history* object is its length. You can use this property to find how many pages the user has visited:
```javascript
alert("You've visited: " + history.length + " web pages in this browser session");
```
The *history* object has three methods.
*forward()* and *back()* are equivalent to passing the Forward and Backward buttons on the browser; they take the user to the next or previous page in the history list.
```javascript
history.forward();
```
The third method, *go*, takes a single parameter. This can be an integer, positive or negative, and it takes the user to a relative place in the history list:
```javascript
history.go(-3); // Go back 3 pages
history.go(2); // Go forward 2 pages
```
The method can alternatively accept a string, which it uses to find the first matching URL in the history list:
```javascript
history.go("example.com"); // Go to the nearest URL in the history
                           // List that contains 'example.com'
```

## Using the *location* Object
The *location* object contains information about the URL of the currently loaded page.
You can think of the page URL as a series of parts:
> [protocol]//[hostname]: [port]/[pathname][search][hash]
----
Here is a sample URL:
> http://www.example.com:8080/tools/display.php?section=435#list
----
The list of properties of the location object includes data concerning the various parts of the URL.
The properties are listed in the Table below.

Property | Description
--- | ---
*location.href* | 'http://www.example.com:8080/tools/display.php?section=435#list'
*location.protocol* | 'http:'
*location.host* | 'www.example.com:8080'
*location.hostname* | 'www.example.com'
*location.port* | '8080'
*location.pathname* | '/tools/display.php?'
*location.search* | '?section=435'
*location.hash* | '#list'

----

## Navigating Using the *location* Object
There are two ways to take a user to a new page using the *location* object.
First you can directly set the *href* property of the object:
```javascript
location.href =  'www.example.com';
```
Using this technique to transport the user to a new page maintains the original page in the browser history list, so the user can return simply by using the browser's Back button.
If you pre
