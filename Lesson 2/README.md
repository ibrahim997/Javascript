# Lesson 2

## Including Javascript in Your Web Page

Previously, you learned that Javascript programs are pased to the browser along with page content. But how exactly is that achieved? Two basic methods associate Javascript code with a HTML page, both of which use the <script></script> element introduced in Lesson 1.

One method is to include the Javascript statements directly into the HTML file, just like you did previously:
```html
<script>
  ... Javascript statements are written here...
</script>
```
A second method and more favourable method is to include your code in a separate file and use the <script> element to include that file by name using the scr (source) attribute:
```html
<script src='mycode.js'></script>
```
The file *mycode.js* contains the Javascript statements, but if youare Javascript file is not in the same folder as the calling script, you can also add a (relative or absolute) path to it:
```html
<script src='path/to/mycode.js'></script>
```
or
```html
<script src='http://www.example.com/path/to/mycode.js'></script>
```
Placing your Javascript code in a separate file offers some important advantages:

* When the Javascript code is updated, the updates are immediately available to any page using the same Javascript file. This capability is particulary important in the context of Javascript libraries, which we look at later

* The code for the HTML page is kept cleaner and therefore is easier to read and maintain

* Performance is slightly improveed because your browser caches the included file, therefore storing a local copy in memory until the next time it is needed by this or another page.

> Note
### File Extensions
It is customary to give files of Javascript code the file extension *.js*, as in this example. However, your included code files can have any extension, and the browser will try to interpret the contents as Javascript.

----

> Caution
### Take Care with Markup
The Javascript statements in the external file must NOT be surrounded by <script> .. </script> tags. In addition, you cannot place any HTML markup within the external file. Just include the raw Javascript code.

----

*Lesson2* shows the simple web page used in Lesson 1, but now with a file of Javascript code included in the <body> section. Javascript can be placed in either the head or body of the HTML page. In fact, it is more common - and generally recommened - for Javascript code to be placed in the head of the page, where it provides a number of functions that can be called from elsewhere in the document. Functions are discussed in Lesson 3.

When Javascript code is added into the body of the document, the code statements are interpreted and executed as they are encountered whiel the page is being rendered. For this reason, it's important that Javascript instructions do not try to access DOM elements that haven't yet been defined. Instead, Javascript must be included *after* the HTML defines such terms.

> Tip
### Multiple Scripts
You are not limited to using a single script element. You can have as many of them on the page as possible.

----

> Note
### HTML Comments
You sometimes see HTML-style comment notation *<! --* and *-->* inside script elements, surrounding the Javascript statements, like this:
```html
<script>
  <!--
    ... Javascript statements are written here ...
  -->
</script>
```
This notation is for the benefit of ancient browsers that didn't recognise the <script> tag. This technique is not required.

----

## Writing Javascript Statements

Javascript programs are lists of individual instructions that we refer to as *statements*. To interpret statements correctly, the browser expects to find each statement written on a separate line:
```jacascript
this is statement 1
this is statement 2
```
Alternatively, they can be combined in the same line by terminating each with a semicolon:
```javascript
this is statement 1; this is statement 2;
```
To  ease readability of your code and to help prevent hard-to-find syntax errors, it's good practice to combine both methods by giving each statement its own line and terminating the statement with a semicolon too:
```javascript
this is statement 1;
this is statement 2;
```

## Commenting Your Code

Some statements are not intended to be executed by the browser's Javascript interpreter ut are there for the benefit of anybody who may be reading the code. We refer to such lines as *comments*, and there are specific rules for adding comments to your code.

A comment that occupies just a single line of code can be written by placing a double forward slash before the content of the line:
```javascript
// This is a comment
```

> Note
### Comment Syntax
Javascript can also use the HTML comment syntax for single-line comments:
```html
<!-- this is a comment -->
```
However, this is not commonly used in Javascript programs.

----

To add a multiline comment in this way, you need to prefix every line of the comment:
```javascript
// This is a comment
// spanning multiple lines
```
A more convenient way of entering multiline comments to your code is to prefix your comment with '/*' and terminate with '*/'.
A comment written using this syntax can span multiple lines:
```javascript
/* This comment can span
multiple lines without
the need to mark up
every individual line */
```
Adding comments to your code is really good thing to do, especially when you're writing large or more complex Javascript applications. Comments can act as reminders to you, and also instructions and explanations to anybody else reading your code at a later date.

> Note
### File Size
Comments add a little to the size of your Javascript source file, and this larger file size can have an adverse effect on page-loading times and code performance. Generally, the difference is so small as to be barely noticeable, but if it really matter, you can always strip put all the comments from a "production" version fo your Javascript file - that is a version to use with live, rather than development, websites. Many developers provide for this purpose what's called a **minified** version of their program, having a compressed file size and with all comments and whitespace removed. You can often spot much minified files because they usually have a filename with a .min.js suffix.

----

## Using Variables

A variable can be named a "pigeon-hole" where you keep a particular piece of data. Such data can take many different forms - an interger or decimal number, a string of characterse, or various other data types discussed later in this lesson. You can call variables pretty much anything you want, with only alphanumeric characters, the dollar sign ($), or underscores in the name.

> Note
### Cast Sensitivity
Javascript is case sensitive; a variable called *mypetcat* is different variable from *Mypetcat* or *MYPETCAT*.
Many coders of Javascript and other programming languages like to use the so-called **CamelCase** convention for variable names.
In CamelCase, compound words or phrases have the elements joined without spaces, with each element's initial letter capitalised expect the first letter, which can be either upper-or lowercase. In this example, the variable would be named *MyPetCat* or *myPetCat*.

----

Suppose you have a variable called *netPrice*. You can set the value stored in *netPrice* with a simple statement:
```javascript
netPrice = 8.99;
```
We call this *assigning a value* to a variable.

> Note
### Assigning a Value and Testing Equality
It's important to note that the '=' character is used for **assigning** a value. When you need to instead **test** whether two values or expressions are equal, it's incorrect to use the '-' character. Instead, you need '==' to test equality:
```javascript
if(a == b) { ..do something.. } // correct, test whether a and b are equal
if(a = b) { ..do something.. } // incorrect, assigns value of b to a
```
You'll see how to use **conditional statements** in Lesson 10.

----

Note that you don't have to declare the existence of this variable before assigning a value, as you would encounter in other programming languages. However, doing so is possible in Javascript. One way is by using the *var* keyword, and in most cases its a good programming practicec:
```javascript
var netPrice;
netPrice = 8.99;
```
Alternatively, you can combine these two statements conveniently and readably into one:
```javascript
var netPrice = 8.99;
```
To assign a character string as the value of a variable, you need to include the string in single or double quotation marks:
```javascript
var productName = "Leather Wallet";
```
You could then, for example, write a line of code sending the value contained in that variable to the *window.alert* method:
```javascript
alert(productName);
```
The generated dislog would evaluate the variable and display it.

> Tip
### Variable Names
Choose readable variable names. Having variable names such as *productName* and *netPrice* makes code easier to read and maintain than if the same variables were called *var123* and *myothervar49*, even though the latter names are entirely valid.

----

## Working with Operators

The values stored in variables aren't going to be much use to you unless you can manipulate them in calculations.

## Arithmetic Operations

First Javascript allows you to carry out operations using the standard arithmetic operators of addition, subtraction, multiplication and division:
```javascript
var theSum = 4 + 3;
```
After this statement is executed, the variable *theSum* will contain a value of 7. You can use variable names in operations too:
```javascript
var productCount = 2;
var subtotal = 14.98;
var shipping = 2.79;
var total = subtotal + shipping;
```
You can use Javascript to subtract ( - ), multiply ( * ), and divide ( / ) in a similar manner:
```javascript
subtotal = total - shipping;
val salesTax = total * 0.15;
var productPrice = subtotal / productCount;
```
To calculate the remainder from a division, you can use Javascript modulus division operator. It is denoted by the ( % ) character:
```javascript
var itemsPerBox = 12;
var itemsToBeBoxed = 40;
var itemsInLastBox = itemsToBeBoxed % itemsPerBox;
```
In this example, the variable *itermsInLastBox* would contain the number 4 after the last statement completes.
Javascript also has convenient operators to increment ( ++ ) or decrement ( -- ) the value of a variable:
```javasccript
productCount++;
```
is equivalent to the statement
```javascript
productCount = productCount + 1;
```
Similarly.
```javascript
items--;
```
is just the same as
```javascript
items = items - 1;
```

> Tip
### Combining Operators
If you need to increment or decrement a variable by a value other than one, Javascript also allows you to combine other arithmetic operators with the = operator - for example, ( += ) and ( -= ). 
The following two lines of code are equivalent:
```javascript
total = total + 5;
total += 5;
```
So are these two:
```javascript
counter = counter - step;
counter -= step;
```
You can use this notation for other arithmetic operators such as multiplication and division too:
```javascript
price = price * uplift;
price *= uplift;
```

----

## Operator Procedure

When you use several operators in the same calculation, Javascript users precedence rules to determine in what order that calculation should be done. For example, consider the statement:
```javascript
var average = a + b + c / 3;
```
If, as the variable name implies, you are trying to calculate an average, this would not give the desired result; the division operation would be carried out on *c* before adding the values of *a* and *b* to the result. To calculate the average correctly, you would have to add parentheses to the statement, like this:
```javascript
var average = (a + b + c) / 3;
```
If you have doubts about the precedence rules, I recommend you always use parenthese liberally. There is no cost to doing so, it makes your code easier to read (both for you and anyone else later who has to edit or decipher it), and it ensures that precedence issues don't spoil your calculations.

> Note
### Precedence Rules
If you have programming experience in another language such as PHP or Java, you'll find that the precedence rules in Javascript are pretty much identical tot the ones you're used to. Find out more by doing some online research.

----

## Using the + Operator with Strings

Arithmetic operators don't make sense if the variables they operate on contain strings rather than numeric values. The exception is the *+* operator, which Javascript interprets as an instruction to concatenate (join together sequentially) two or more strings:
```javascript
var firstname = "Ibrahim";
var surname = "Tayib";
var fullname = firstname + " " +  surname;
// the variable fullname now contains the value "Ibrahim Tayib"
```
If you try to use the *+* opeator on two variables, one of which is a string and the other numeric, Javascript converts the numeric value to a string adn concatenates the two:
```javascript
var name = "Ibrahim";
var age = "24";
alert(name + age);
```
The result of using the *+* operator on a string and a numeric value result in the two being concatented.

## Try It Yourself
### Convert Celsius to Fahrenheit

Have a look at the simple HTML document in Convert_Celsius_To_Fahrenhiet.html

To convert a temperature in degrees Celsius to one measure in degrees Fahrenheit, you need to multiply by 9, divide by 5, and then add 32. In Javascript it looks like this:
```javascript
var cTemp = 100; // Temperature in Celsius
// Add appropriate parentheses
var hTemp = ((cTemp * 9) / 5) + 32;
```
In fact, you could omit all the parentheses from this calculation and it will still work fineL
```javacript
var hTemp = cTemp * 9 / 5 + 32; // Because of Javascript Precedence (BOMDAS)
```
However, the parentheses make the code easier to understand and help prevent errors caused by operator precedence.

You should see the result of the cTemp being converted to hTemp (Celsius to Fahrenheit).

## Capturing Mouse Events

One of the fundamental purposes of Javascript is to help make your web pages more interactive for the user. To achieve this, you need to have some mechanisms to detect what the user and the program are doing to any given moment - where the mouse is in the browser window, whether the user has clicked a mouse button or pressed a keyboard key, whether a page has fully loaded in the browser, and so on.

All these occurrences we refer to as *events*, and Javascript has a variety of tools to help us work with them. Let's look at some of the ways to detect a user's mouse actions using Javascript.

Javascript deals with events using so-called handlers. We are going to investigate three of these: *onClick*, *onMouseOver*, and *onMouseOut*.

## The *onClick* Event Handler

The *onClick* event handler can be applied to nearly all HTML elements visible on a page. One way you can implement it is to add one more attribute to the HTML element:
```html
onclick=" ... some Javascript code .. "
```

> Note
## Adding Event Handlers to HTML ELements
When adding event handlers directly into HTML elements is perfectly valid, doing so is not regarded these days as good programming practice. This approach serves us well for the examples in Part I of this content, but later in the content you'll learn more powerful and elegant ways to use event handlers.

----

Look at the example in onClick.html, for an onClick demo.

The HTML code adds a button to the <body> element of the page and supplies that button with an *onclick* attribute. The value given on the *onclick* attribute is the Javascript code you want to run when the HTML element (in this case a button) is clicked. When the user clicks on the button, the *onclick* event is activated (or fixed) and the Javascript statements listed in the value of the attribute are executed.

In the case of the onClick.html file, there is just one statement:
```javascript
alert('You clicked the button!)
```

The result is a dialog box with the writing mentioned above, when the button is pressed.

> Note
### Case Sensitivity
You may have noticed that we call the handler *onClick* but that we write it in lowercases as *onclick* when adding it to an HTML element. This convention has arisen because, although HTML **is not** case sensitive, XHTML **is** case sensitive and requires all HTML elements and attribute names to  be written in lowercase.

----

## *onMouseOver* and *onMouseOut* Event Handlers

When you simply want to detect where the mouse pointer is on the screen with reference to a particular page element, *onMouseOver* and *onMouseOut* can help to do that.

The *onMouseOver* event is fired when the user's mouse cursor enters the region of the screen occupied by the element in question. The *onMouseOut* event, is fired when the cursor leaves the same region.

Look at the example in onMouseOver.html, for onMouseOver demo.

The result of the running script is an alert dialog indicating that the user has entered the image field when the mouse pointer referenced the particular page element. Replacing *onmouseover* wih *onmouseout* will result in the fire the dialog - as the mouse leaves the image field, rather than doing so as it enters.

## Try It Yourself
### Creating an Image Rollover

Have a look at the simple HTML document in Image_Rollover.html

You can use the *onMouseOver* and *onMouseOut* events to change how an image appears while the mouse pointer is above it. To achieve this, you can use *onMouseOver* to change the *src* attribute of the HTML tag <img> element as the mouse cursor enters and *onMouseOut* to change it back as the mouse cursor leaves.

You may notice something new in the syntax used here. Wthin the Javascript statements for *onMouseOver* and *onMouseOut* is the keyword *this*.

When you use *this* within an event handler added via an attribute of an HTML element, *this* refers to the HTML element itself; in this case, you can read it as "this image", and *this.src* refers (using the "dot" notation) to the *src* (source) property of this image object.

In this example we used two images - tick.gif and tick2.gid. You can use any images you have on hand but the demonstration works best if they are the same size and not too large.

Use your editor to create an HTML file containing the code of Image_Rollover.html. You can change the image name tick.gif and tick2.gif to the names of your own two image; just ensure the images are saved in the same folder as the HTML file. Save the HTML file and open it in the browser.

You should see the image change as the mouse pointer enters and changes back as it leaves.

> Note
### Image Rollovers
At one time image rollovers were regularly done this way, but these days they can be achieved much more efficiently using Cascading Style Sheets (CSS). Still, it's convenient way to demonstrate the use of the *onMouseOver* and *onMouseOut* event handlers. You'll learn about using CSS with Javascript in later lessons.

## Summary

You learned about various ways to include Javascript code in your HTML code.

You studied how to declare variables in Javascript, assign values to those variables, and manipulate them using arithmetic operators.

Finally, you used some of Javascript event handlers and learned how to detect certain actions of the user's mouse.

## Exercises

Startitng with onMouseOver.html, remove the *onMouseOver* handler from the <img> element. Instead add an *onClick* handler to set the title property of the image to *My New Title*. (Hint: you can access the image title using *this.title*).

Can you think of an easier way to test whether your script has correctly set the new image title?
