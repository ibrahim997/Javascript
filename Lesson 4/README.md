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

