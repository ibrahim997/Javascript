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


