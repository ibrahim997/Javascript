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
In this example, the variable *itermsInLastBox* would contain the number 4
