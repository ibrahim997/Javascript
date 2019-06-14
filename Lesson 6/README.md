## Lesson 6

## Dealing with Numbers
We use the term *data type* to explain tha nature of the data that a variable contains. A string variable contains a character string, a number variable contains a numerical value, and so forth. However, the Javascript language is loosley typed, meaning that the variables can be interpreted as different data types in differing circumstances.

## Numbers
There are many different types of numbers, *natural numbers* (1,2,3,4..), *whole numbers* (simply add 0) and *negative numbers* which form the set of *integers*.

To express numbers falling between integers, you commonly use a decimal point with one or more digits following it: (3.14159264). Such numbers are called *floating point* numbers indicating they have an arbitary number of digits before and after the decimal point, that is the decimal point can float to any location in the number.

## Integers
An integer is a whole number - positive, negative, or zero. In other words, an integer is a numerical value without a fractional part.

## Floating-Point Numbers
Floating-point numbers have a fractional part, even if that fractional part is zero. They can be represented in the traditional way or exponential notation.

> Note
### Exponential Notation
In exponential notation, e, represents "times 10 to the power", so 35.4e5 can be read as 35.4 x 10^5. It provides a compact way of expressing numbers from the very large to the very small. 

----

## Hexadecimal, Binary and Octal Numbers
Javascript also has the capability to handle hexadecimal (base 16), binary (base 2), and octal (base 8) numbers. In addition to the more familiar decimal (base 10) numbers.

Hexadecimal numbers begin with the prefix 0x - for instance, 0xFF represents the number 255.

Binary values are prefixed with 0b, such as 0b111, which represents 7.

Octal (base 8) numbers are perhaps less common, but they too can be used in programs. You prefix an octal number with 0o (zero followed by lowercase letter o), so for instance 0o77 is the octal representation for 63.

> Note
### Unix-style File Permissions
With Unix operating systems or one of its siblings such as Linux, or Mac OS. The read, write and execute (rwx) permissions allocated to files in such systems are each associated with the three bits of a binary number. The resulting binaries are more often shown as octal values as follows:

Octal Digit | Binary (rwx) | Permission
--- | --- | ---
0 | 000 | none
1 | 001 | execute only
2 | 010 | write only
3 | 011 | write and execute
4 | 100 | read only
5 | 101 | read and execute
6 | 110 | read and write
7 | 111 | read, write, and execute

----

## Global Methods
Javascript has a range of methods available for use in manipulating numerical values. These are *global* methods; that is, they are available at any point in the code.

> Note
### Primitive Value Can Use Methods
So-called primitive values such as numbers are not objects so cannot have their own properties and methods. But Javascript treats primitive values as objects, thus enabling the execution of the methods described in this section.

Let's dive into some of these methods.

## *toString()*
The *toString()* method returns a number as a character string. Let's look at how the conversion works.

The method works just fine on either a variable or when directly applied to a numerical value:
```javascript
var num = 666;
num.toString(); // Returns string "666"

(666).toString(); // Returns string "666"
```
You can use *toString()* directly with an expression too:
```javascript
(333 * 2).toString(); // Returns string "666"
```

> Tip
### Using a Radix with *toString()*
The *toString()* method can optionally be pressed an argument, an integer between 2 and 36, as a radix value.
