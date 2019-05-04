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
