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

If you prefer that the sending page is removed from the history list and replaced with the new URL, you can instead use the location object's *replace* method:
```javascript
location.replace('www.newpage.com');
```
This method replaces the old URL with the new one both in the browser and in the history list.

## Reloading the Page
To reload the current page into the browser - the equivalent of having the uesr click the "reload" button - you can use the *reload* method:
```javascript
location.reload();
```

> Tip
### Avoiding Cache Problems
Using *reload()* without any arguments retrieves the current page from the browser's cache, if it's available there. To avoid this and get the page directly from the server, you can call *reload()* with the argument *true*:
```javascript
document.reload(true);
```

----

## Obtaining Browser Information - The *navigator* Object
Whereas the *location* object stores information about the current URL loaded in the browser, the *navigator* object's properties contain data about the browser application itself.

## Try It Yourself
### Displaying Information Using the *navigator* Object
We're going to write a script that allows you to find what the *naviagtor* object knows about your own browsing setup. Use your editor to create a file navigator.html containing the code from using_nav_object.html containing the code.

The result is that the object provides, at best, an unreliable source of information about the user's platform. Not all properties are supported in all browsers, and the names reported for browser type and version rarely what you would intuitively expect.

## Using Dates and Times
The *Date* object is used to work with dates and times. There is no *Date* object created for you as part of the DOM, as was the case with examples thus far. Instead you create your own *Date* object as when you need them. Each *Date* object you create can represent a different date and time.

## Creating a *Date* Object with the Current Date and Time
The simplest way to create a new *Date* object containing information about the date and time looks like this:
```javascript
var mydate = new Date();
```
The variable *mydate* is an object containing information about the date and time at the moment the object was created. Javascript has a long list of methods for retrieving, setting and editing data within Date objects. Let's look at a few simple examples:
```javascript
var year = mydate.getFullYear(); // Four-digit year e.g. 2019
var month = mydate.getMonth(); // Month number 0 - 11; 0 is Jan, etc.
var date = mydate.getDate(); // Day of the month 1 - 31
var day = mydate.getDay(); // Day of the week 0 - 6; Sunday = 0, etc.
var hours = mydate.getHours(); // Hours part of the time, 0 - 23
var minutes = mydate.getMinutes(); // Minutes part of the time, 0 - 59
var seconds = mydate.getSeconds(); // Seconds par of the time, 0 -59
```

## Creating a *Date* Object with a Given Date and Time
You can easily create *Date* objects representing arbitrary dates and times by passing arguments to the *Date()* statement. There are several ways to do this:
```javascript
new Date(milliseconds) // Milliseconds since Jan 1st 1970
new Date(dateString)
new Date(year, month, day, hours, minutes, seconds, milliseconds)
```
Here are some examples.

You can use a date string like this:
```javascript
var d1 = new Date("October 22, 1995 10:57:22");
```
When you use separate arguments for the parts, trailing arguments are optional; any missing arguments replaced with zero:
```javascript
var d2 = new Date(95,9,222) // 22nd October 1995 00:00:00
var d3 = new Date(95,9,22,10,57,0) // 22nd October 1995 10:57:00
```

## Setting and Editing Dates and Times
The *Date* object has an extensive list of methods for setting or editing the various parts of the date and time:
```javascript
var mydate = new Date(); // Current date and time
document.write("Object created on day number " + mydate.getDay() + "<br />");
mydate.setDate(15); // Change the day of month to the 15th
document.write("After amending date to the 15th, the day number is " + mydate.getDay());
```
The preceding code snippet initially creates the object *mydate* representing the date and time of its creation, but with the day of the month subsequently changed to the 15th; if you retrieve the day of the week before and after this operation, you'll see that it has been correctly recalculated to take account of the changed date:
```javascropt
// Result:
// Object created on day number 5
// After amending date to 15th, the day number is 0
```
You can also carry out date and time arthimetic, letting the *Date* object do all the heavy lifting:
```javascript
var mydate = new Date();
document.write("Created: " + mydate.toDateString() + " " + mydate.ToTimeString() + "<br />");
mydate.setDate(mydate.getDate(0 + 33); // Add 33 days to the 'date' part
document.write("After adding 33 days: " + mydate.toDteString() + " " + mydate.toTimeString());
```
The preceding example calculates a date 33 days in the future, automatically amending the day, month, and/or year as necessary. Note the use of *toDateString()* and *toTimesString()* they are useful methods for converting dates into a readable format.

## Simplifying Calculation with the *Math* Object
Javascript's *Math* object can save you a lot of work when performing calculations that frequently occur.

Unlike *Date* object, the *Math* object does not need to be created before use; it already exists, you can its methods directly.

Table below shows some of the methods available.

Method | Description
--- | ---
*ceil(n)* | Returns *n* rounded up to the nearest whole number
*floor(n)* | Returns *n* rounded down to the nearest whole number
*max(a,b,c,..)* | Returns the largest number
*min(a,b,c,..)* | Returns the smallest number
*round(n)* | Returns *n* rounded up or down to the nearest whole number
*random()* | Returns a random number between 0 and 1

Let's work through some examples.

## Rounding
The methods *ceil(), *floor()*, and *round()* are useful for truncating the decimal parts of numbers:
```javascript
var myNum1 = 12.55;
var myNum2 = 12.45;
alert(Math.floor(myNum1)); // Shows 12
alert(Math.ceil(myNum2)): // Shows 13
alert(Math.round(myNum1)); // Shows 13
alert(Math.round(myNum2)); // Shows 12
```
Note that when you use *round()*, if the fractional part of the number is 0.5 or greater, the number is rounded to the next highest integer. If the fractional part is less than 0.5, the number is rounded to the next lowest integer.

## Finding Minimum and Maximum
You can use *min()* and *max()* to pick the largest and smallest number from a list:
```javascript
var ageDavid = 23;
var ageMary = 27;
var ageChris = 31;
var ageSandy =19;
document.write("The youngest person is " + Math.min(ageDavid, ageMary, ageChris, ageSandy) + " years old<br />");
document.write("The oldest person is " + Math.max(ageDavid, ageMary, ageChris, ageSandy) + " years old<br />");
```

## Generating Random Numbers
To generate a random number, you can use *Math.random()*, which generates a random number beween 0 and 1.

Normally, you would specify the possible range of numbers; for example, you might want to generate a random number between 0 and 100.

As *Math.random()* generates a random number between 0 and 1, it's helpful to wrap it in a small function that suits your needs. The following function takes the *Math* object's randomly generated number, scales it up by multiplying by the variable range (passed to the function as an argument), and finally uses *round()* to remove any fractional part:
```javascript
function myRand(range) {
  return Math.round(Math.random() * range);
}
```
To generate a random integer between 0 and 100, you simply call:
```javascript
myRand(100);
```

> Caution
### Use *Math* Methods Directly
You always use *Math* methods directly,for example, *Math.floor()* , rather than as a method of an object you created. In other words:
```javascript
var myNum = 24.77;
myNum.floor();
```
The code would provoke a Javascript error.

Instead,
```html
<p>Math.floor(myNum);</p>
```
will work correctly.

----

## Mathematical Constants
Various often-used mathematical constants are available as properties of *Math*. They are listed below.

Constant | Description
--- | ---
E | Base of natural logs, approx. 2.718
LN2 |  Natural log of 2, approx. 0.693
LN10 | Natural log of 10, approx. 2.302
LOG2E | Base 2 log of E, approx. 1.442
LOG10E | Base 10 log of E, approx. 0.434
PI | Approx. 3.14159
SQRT1_2 | 1 over the square root of 2, approx.0.707
SQRT2 | Square root of 2, approx. 1.414

These constants can be used directly in your calculations:
```javascript
var area = Math.PI * radius * radius; // Area of circle
var circumference = 2 * Math.PI * radius; // Circumference
```

## The *with* Keyword
Although you can use the *with* keyword with any object, the *Math* object is an ideal object to use as an example. By using *with*, you can save yourself time.

The keyword *with* takes an object as an argument and is followed by a code block wrapped in braces. The statements within that code block can call methods without specifying an object, and Javascript assums that those methods belong to the object passed as an argument.

Here is an example:
```javascript
with (Math) {
  var myRand = random();
  var biggest = max(3,4,5);
  var height = round(76.35);
}
```
This examples calls *Math.random()*, *Math.max()*, and *Math.round()* simply by using the method names, because all method calls in the code block have been associated with the *Math* object.

## Try It Yourself
### Reading the Date and Time
We are going to create a script to get the current date and time when the page is loaded. You can also implement a button to reload the page to refresh the time and date information.

Take a look at reading_date_time.html.

The first statement in the function *tellTime()* creates a new *Date* object called *now*. Since the object is created without passing any parameters to Date(), it will have properties pertaining to the current date and time at the moment of its creation.
```javascript
var now = new Date();
```
You can access the individual parts of the time and date using *getDate()*, *getMonth()*, and similar methods. As you do so, you assemble the output message as a string stored in the variable *out*:
```javascript
out += "<br />Date: " + now.getDate();
out += "<br />Month: " + now.getMonth();
out += "<br />Year: " + now.getFullYear();
out += "<br />Hours: " + now.getHours();
out += "<br />Minutes: " + now.getMinutes();
out += "<br />Seconds: " + now.getSeconds();
```
Finally, you use *getElementById()* to select the (initally empty) *div* element having *id="div1"*, and write the contents of variable *out* into it using the *innerHTML* method:
```javascript
document.getElementById("div1").innerHTML = out;
```
The function *tellTime()* is called by a small script embedded in the *body* part of the page:
```html
<script>
    tellTime();
</script>
```
To refresh the page, simply reload the page into the browser. At this point, the script runs again, creating a new instance of the *Date* object with the current date and time. Using the *location* object you can do the following to reload the page using a button:
```html
<input type="button" onclick="location.reload()" value="Refresh" />
```
Remember that Javascript counts months starting from 0 (Jan) and ending in 11 (Decemeber).

## Summary
You saw how to use the *window* object's modal dialogs to exchange information with the user.

You also learned how to select a page elements by their ID using the *document.getElementById()* method, and how to get and set the HTML inside a page element using the *innerHTML* property.

In addition, you worked with the browser information from the *navigator* object and page URL information from the *location* object.

Finally, you saw how to use the *Date* and *Math* objects.
