# Lesson 1

## Introduction

Hypertext Markup Language is not a programming language but a markup language.
You can use it to mark parts of your page to indicate to the browser that these
parts should be shown in a particular way - using bold or italic text, for instancec, or
as a heading, alist of bullet points, a table of data, or using manyn other markup options.

Once these pages are written they are static by nature. They can't respond to user actions,
make decisions, or modify the display of their page elements. The markup they contain will always
be interpreted and dislpayed in the same way whenever a user vists the page.

The World Wide Web contains modern websites that much more and routinely visit are often
far more than static. They can contain "live" data, such as share prices or flight arrival times,
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

## The '<script>' tag
