# Lesson 1

## Introduction

Hypertext Markup Language is not a programming language but a markup language.
You can use it to mark parts of your page to indicate to the browser that these
parts should be shown in a particular way - using bold or italic text, for instancec, or
as a heading, alist of bullet points, a table of data, or using manyn other markup options.

Once these pages are written they are static by nature. They can't respond to user actions,
make decisions, or modify the display of their page elements. The markup they contain will always
be interpreted and dislpayed in the same way whenever a user vists the page.

The World Wide Web contains modern websites that can do much more and the pages we routinely visit are often
far from static. They can contain "live" data, such as share prices or flight arrival times,
animated displays with changing colors and fonts, or interactive capabilities such as the ability
to click through a gallery of photographs or sort a column of data.

These capabilities are provided to the user through programs, often known as scripts 
that operate behind the scenes to manipulate what is being displayed on the browser.

## Server vs. Client-side Programming

There are two fundamental ways of adding scripts to otherwise a static web content:
> A web server executes a script before delivering the page to the user. Such script may define what 
  information is sent to the browser for display to the user - for example, by retrieving product prices
  from the database of an online store, checking a user's identity cedentials before loggin her in to a private
  area fo the website, or retrieving the contents of an email mailbox.
  These scripts are generally run at the web sever before generating the requested web page and serving
  it to the user. This particular way of adding script is known as *server-side* scripting.

> Alternatively, the script rather than being run on a web server, can be delivered to the user's browser
  along with the markup code that defines the page. Such scripts operate on the page's already-delivered content
  and is executed by the browser.
  The many functions these scripts perform include: animating page sections, reformatting page layouts, allowing
  user to drag and drop items within a page, validating user input on forms, redirecting users to other pages,
  and much more. This alternative is known as *client-side* scripting.

## Javascript in a Nutshell

A program written in Javascript can access the elements of a web page and the browser window in which it is running.
It also can perform actiosn on these elements and create new page elements. A few examples of Javascript capabilities include:
* Opening a new windows with specified size, position, and style (for exmaple, whether the window has borders, menus, toolbars etc.)
* Providing uesr-friendly navigation aids such as drop-down menus
* Validating data entered into a web form to make sure that it is of an acceptable format before the form is submitted to the web server
* Changing how page elements look and behave when particular events occur, such as the mouse cursor moving over them
* Detecting and exploiting advanced features supported by the particular browser being used, such as third-party plug-ins or native support for new technologies

Because Javascript code runs locally inside the user's browser, the page tends to respond quickly to Javascript instructions, enhancing the user's experience and making the application seem more like one of the computer's native applications than simply a web page. Also, Javascript can detect and utilise certain user actions that HTML can't, such as individual mouse clicks and keyboard actions.

## The <script> tag

Whenever a user requests a page, any Javscript programs that page contains are passed to the browser along with page content. 
Inclduing Javascript statements directly into the HTML code is done by placing them between <script> and </script> tags within the HTML:
```javascript
<script>
  ...Javascript statements...
</script>
```
>Note
### Interpreted and Compiled Languages

Javascript is an interpreted language, rather than a compiled language such as C++ or Java. This means that the Javascript instructions are passed to the browser as plain text and are interpreted sequentially; the do not need to first be "compiled" into condensed machine code only readable by the computer's processor. This capability offers big advantage in that Javascript programs are easy to read, they can be edited swiftly, and their operation can be retested simply be reloading the web page in the browser.

The examples in this lesson place Javascript code within the <body> section of HTML document, but Javascript code can appear elsewhere in the document too; you can also use <script> to load Javascsript code stored in an external file.

## Introducing the DOM

A Document Object Model (DOM) is a conceptual way of visualising a document and its contents.

Each time a web browser is asked to load and display a page, it needs to interpret (*parse*) the source code contained in the HTML file comprising the page. As part of this parsing process, the browser creates a type of internal model known as DOM representation based on the content of the loaded document. It is this model that the browser then refers to when rendering the visible page. You can use Javascript to access and edit the various parts of the DOM representation, at the same time changing the way the user sees and interacts with the page in view.

## The *window* and *document* Objects

Each time a browser loads and displays a page, it creates in memory an internal representation of the page and all its elements, the DOM. In the DOM, elements of your web page have a logical, heirarchical structure, like a tree of interconnected patent and child objects. THese objects, and their interconnections, form a conceptual model of the web page and the browser that contains and displays it. Each object also has a list of properties that describe it, and a number of methods you can also use to manipulate those properties using Javascript.

Right at the top of the hierarchical tree is the browser *window* object. This object is a parent or ancestor to everything else in the DOM representation of your page.

The *window* object has various child objects. The first child object and the one that will be used for more frequently is the *document* object. Any HTML page loaded into the browser creates a *document* object containing all the HTML and other resources that go into making up the displayed page. ALl this information is accessible via Javascript as a parent-child hierarchy of objects, each with its own properties and methods.

The other children of the *window* object are the *location* object (containing details of the URL of the currently loaded page), the *history* object (containing details of the browser's previously visited pages), and the *navigator* object (which stores details of the browser type, version, and capabilities). We'll look in detail at these objects in Lesson 5.

## Object Notation

The notation to represent objects within the tree uses the dot or period:
```javascript
parent.child
```

As an example, the *location* object is referred to as a the child of the *window* object, so in the DOM it is referred to like this:
```javascript
window.location
```

>Tip
### Extending DOT Notation

This notation can be extended as many times necessary to represent any object in the tree.
For example,
```javascript
object1.object2.object3
```
represents *object3*, whose parent is *object2*, which itself is a child of *object1*. 

Since the <body> section of a HTML page is represented in the DOM as a child element of the *document* object, you would access it like this:
  ```javascript
  window.document.body
  ```
The last item in the sequence can also be, istead of another object, a propertyor method of the parent object:
  ```javascript
  object1.object2.property
  object1.object2.method
  ```
For example, suppose that you want to access the *title* property of the current document, as specified by the HTML <title>...</title> tags. You simply use:
  ```javascript
  window.document.title
  ```

>Tip
#### A Handy Shortcut
The *window* object always contains the current browser window, so you can refer to *window.document* to access the current document. As a shortcut, you can also simply use *document* instead of *window.document*; this also refers to the current document.
If you have several windows open, or if you are using a frameset, separate *window* and *document* object exist for each window or frame. To refer to one of these documents, you need to use the relevant window name and document name belonging to the window or frame.

## Talking to the User

Methods associated with the *window* and *document* objects which provides a means of talk to the user include:
```javascript
window.alert
```
The *window* object, is at the top of the DOM hierarchy and represents the browser window that's displaying the page. WHen you call *alert()* method, the browser pops open a dialog displaying your message, along with an OK button. Here is an example:
```javascript
<script>window.alert("Here is my message");</script>
```
This is the first working example of the dot notation. Here we are calling the *alert()* method of the *window* object, so our object.method notation becomes *window.alert*.

>Tip
#### Another Handy Shortcut
You can leave the *window* object out of the statement. Because the *window* object is the top of the DOM hierarchy (sometimes referred to as **global object**), any methods called without direct reference to their parent object are assumed to belong to the *window* object. Therefore:
```javascript
<script>alert("Here is my message")</script>
```
Works fine!

Notice that the line of text inside the parentheses () is contained within quotation marks. These can be single or double qoutes, but they must be there; otherwise, an error will be occur.

This line of code, when executed in the browser, pops up a *window.alert()* dialog.

>Tip
#### Understanding Model Dialogs
Until the user clicks OK, they are prevented from doing anything else. A dialog that behaves this way is known as a model dialog.

## document.write()

The *write* method of the *document* object instead of popping up a dialog, writes characters directly into the DOM of the document.
```javascript
<script>document.write("Here is another message");<script>
```

>Note
In fact, *document.write* is not a favourable way of writing content to the page; it has loads of limitations, both in terms of functions and in terms of coding style and maintainability. It has largely fallen into disuse for Javascript programming. It will be used for only showing the basic principles of the language.

----
# Try It Yourself
### See Lesson1.html
----


