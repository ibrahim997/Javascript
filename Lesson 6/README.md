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
With Unix operating systems or one of its siblings such as Linux, or Mac OS. The read, write and execute (rwx) permissions allocated to files in such systems are each associated with the three bits of a binary number. 
