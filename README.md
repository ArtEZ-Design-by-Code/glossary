[toc]

# Introduction

This glossary applies to all programming languages, but examples are given in Java / Processing. Pay attention to the capitalization of certain terms or keywords.

## A note on style

There are two extremely important things to keep in mind when writing code, that have to do with the readability of your code and therefore your ability to track down bugs. The first is capitalization. We always use so called *camelCase* for our variable and function names (no capital for the first word and each subsequent word is capitalized), and *SentenceCase* for class names (every word is capitalized).

```java
int legalDrinkingAge = 18;

void checkAirplaneVelocity() {
	...
}

class FootballStadium {
	...
}

FootballStadium cruyffArena = new FootballStadium();
```

The other note is on indentation. Make sure you always indent properly (each line has the appropriate amount of whitespace preceding it). As a guideline, each time you narrow down scope, you indent the next line with one more tab. In Processing, you can automatically reindent your code by pressing `cmd + t`. Also, introduce whitespace by adding empty lines to make your code more readable.

```java
// Wrong:
int myAge = 12;
	void setup() {
int yourAge = 16;
println(yourAge + myAge);
}

// Right:
int myAge = 12;

void setup() {
	int yourAge = 16;
	println(yourAge + myAge);
}
```

Note how much clearer the second example is compared to the first.

# Comments

A comment is a piece of code that is ignored by the computer. It can be used to add some human-readable notes or comments to your code, to clarify what a specific line is doing, or to temporarily disable a line of code.

```java
doSomething();
// After doing something, I want to do something else.
doSomethingElse();
```

# Variables

Variables are used for storing values. They are made up of three components: a *type*, a *name*, and a *value*.

```java
   int    numberOfStudents = 5    ;
// type   name               value
```

The nice thing about variables is that they can be reused throughout your code, so you don't have to repeat values over and over again. Also, they can be changed by your code, so they are dynamic.

```java
int numberOfStudents = 5;

// Someone comes in late. We should update our number to reflect this change.
numberOfStudents = 6;
// We omit the type identifier, because our code already knows that numberOfStudents is an int.
```

## Types

This is not a complete list of types, but these are the ones you will be using the most.

### General

```java
int numberOfStudents = 5;
// Stores a non floating point value (i.e. a number with no decimals).

float currentTemperature = 17.3;
// Stores a floating point value (i.e. a number with decimals).

boolean currentlyRaining = false;
// Stores a boolean value (i.e. either true or false).

char lastKeyPressed = 'c';
// Stores a single character. Note the use of single quotes.
```

### Processing-specific

```java
color buttonColor = color(255, 0, 0);
// Stores a color (in this case red).

String essayTitle = "On the Origin of Species";
// Stores a String (i.e. a string of characters). Note the use of double quotes.
```

# Scope

With scope, you can limit the access to your variables and functions. Scope is created by enveloping your code in between *curly braces*. This is best explained with some examples.

```java
int age = 53;
// In the so-called global scope

void printAge() {
	int yearsOfWorkExperience = 32;
	// Only available within the printAge function
	
	println("Started working at the age of " + (age - yearsOfWorkExperience));
	// Will print "Started working at the age of 21"
}

void brokenFunction() {
	println("Has worked for " + yearsOfWorkExperience);
	// Will give an error, because yearsOfWorkExperience cannot be found in the current scope.
}
```

Functions, loops, conditionals and such all create scope. You can also define a new scope anywhere, by using curly braces.

```java
void myFunction() {
	int myNumber = 5;
	
	{
		int otherNumber = 6;
	}
	
	println(myNumber + otherNumber);
	// Will give an error, because otherNumber cannot be found in the current scope.
}
```

# Functions

A function is a piece of code that performs a specific function. They optionally take some input, do something, and then optionally return some output. This means that we have to tell the computer what type of inputs and outputs it can expect.

## General

The simplest example takes no input and has no output, it just performs some action. In this case, it says hello.

```java
void greet() {
	println("Hello world!");
}
```

Let's focus on the first line of this piece of code.

As you can see, we use the `void` keyword. This is called the *return type* of the function: it is the type of value that the function will return. In this case, the function does not return anything. Void means emptiness, or 'nothing'.

Next up, we give the function a name: in this case, `greet`. Try to always give your functions and variables meaningful names that describe what they do.

Then come the round braces, called *parentheses*: `()`. They contain all the *attributes*, or input variables, that the function expects. In this case, there are none.

Finally, we declare create the scope for the function, which is of course denoted by the curly braces: `{}`. The actual code that does something is written in between these braces. The attributes of the function are available only within this scope.

## Attributes

Now for a slightly more interesting example. Let's say hello to somebody in particular.

```java
void greet(String name) {
	println("Hello, " + name + "!");
}
```

As you can see, we now take some input: a String. This function has one attribute. Each attribute has a *type* and a *name*.

Both of these examples contain just the function *declaration*, so nothing will happen when you run them. The computer now knows how to greet somebody, but we still have to tell it when to actually do this: when to *execute* the function.

```java
greet("John Doe");
// The computer will now print "Hello, John Doe!"
```

The actual *value* of the attribute `name` is passed during the function call itself.

Multiple attributes can be defined by seperating them with commas.

```java
void greet(String personA, String personB) {
	println("Hello, " + personA + " and " + personB + "!");
}
```

## Returning values

In some cases, a function will not only take some input in the form of attributes, but also generate some output in the form of a *return value*.

```java
int addTogether(int numberA, int numberB) {
	int result = numberA + numberB;
	
	return result;
}
```

Two things to consider here: first, instead of having a `void` function, this function will actually return a value. This value will be of the `int` type. See the first line.

Next up, at the end of the function body, we have to actually return the value, which must be of the return type we specified: `return result;`.

# Operators

Operators manipulate values.

## Arithmetic

Arithmetic operators perform basic mathematical operations. They are: `+`, `-`, `/`, `*`, and `%`.

```java
println(5 + 5); // 10
println(7 * 3); // 21
println(7 * 3 + 4 / 2); // 23
println(16 % 5); // 1
```

That last one (`%`) is the *modulo* operator. It calculates the remainder after a division. So for example, 16 % 5 is calculated as follows: 16 divided by 5 is 3 with a remainder of one (`5 * 3 + 1 == 16`). So 16 % 5 is 1.

## Assignment

Assignment operators assign a value to a variable. They are: `=` (assign), `+=` (add and assign), `-=` (subtract and assign), `*=` (multiply by and assign), `/=` (divide by and assign), and `%=` (modulo by and assign).

```java
int myValue = 5;
println(myValue); // 5

myValue += 2;
println(myValue); // 7

myValue *= 2;
println(myValue); // 14
```

## Unary

Unary operators increment, decrement or invert a value. They are: `++` (increment), `--` (decrement), and `!` (invert).

```java
int myValue = 6;
println(myValue); // 6

myValue++;
println(myValue); // 7

boolean isRaining = true;
boolean wantToGoOutside = !isRaining;

println(wantToGoOutside); // false
```

## Relational

Relational operators compare values. They are: `>` (greater than), `<` (less than), `<=` (less than or equals), `>=` (greater than or equals), `==` (equals) and `!=` (does not equal).

```java
println(5 > 2); // true

int myAge = 15;
int drivingAge = 16;

println(myAge >= drivingAge); // false

int yourAge = 15;

println(myAge == yourAge); // true
println(myAge != yourAge); // false
```

## Logical

Logical operators combine booleans. They are: `&&` (logical AND) and `||` (logical OR).

```java
boolean sunshine = true;
boolean isRaining = false;

println(sunshine && !isRaining); // true

boolean isMarried = true;
boolean livingTogether = false;

println(isMarried || livingTogether); // true
```

## Ternary

Ternary operators take three arguments. The first argument is the comparison argument, the second argument is returned if the first argument evaluates to `true` and the third argument is returned if the first argument evaluates to `false`. The operators are: `?` and `:` and they are always used together.

```java
boolean sunshine = true;
boolean isRaining = false;

String todo = sunshine && !isRaining ? "Go to the beach" : "Stay inside";
```

# Arrays

An array is basically a collection of values of the same type. An array always has a type, a name, and a length (size). The size of the array cannot be changed, but the values stored in the array can. Arrays are created and referenced using *square brackets*: `[]`. Each *element* of the array has an index (the position the element has on the list) and a value. Note that arrays are zero-indexed: the first element of the array has an index of 0. The highest index in an array with length 6 is therefore 5.

```java
String[] names = new String[6];

names[0] = "Jack";
names[1] = "Kate";
names[2] = "James";
names[3] = "Charlie";
names[4] = "John";
names[5] = "Claire";

println(names[3] + " and " + names[5] + " are together."); // "Charlie and Claire are together."

names[4] = "Jeremy";

println("John is now " + names[4]); // "John is now Jeremy"
println(names.length); // 6
```

# Conditionals

Conditionals can be compared to a fork in the road. If certain conditions are met, one path can be taken, otherwise, take the other path. The conditional expects a *condition*. If the condition *evaluates to* `true`, the block of code is executed.

```java
boolean isItRaining = true;
boolean isThereSunshine = true;

if (!isItRaining && isThereSunshine) {
	println("Go to the beach!");
} else if (isItRaining) {
	println("It's raining, stay inside!");
} else {
	println("It's not raining, but there is no sunshine. Blurgh.");
}
```

# Loops

Loops are used to repeat a block of code. There are two types: `while` and `for`. We use `while` when we want to loop something as long as a certain condition is met, and we use `for` when we want to loop a specific number of times.

A while loop only accepts a condition as its argument.

```java
boolean eyesOpen = true;

while (eyesOpen) {
	println("You've got your eyes open!");
	
	if (random(1000) > 900) {
		eyesOpen = false;
	}
}

println("Ha, you blinked!");

// "You've got your eyes open!"
// "You've got your eyes open!"
// "You've got your eyes open!"
// "You've got your eyes open!"
// "You've got your eyes open!"
// "You've got your eyes open!"
// "You've got your eyes open!"
// "Ha, you blinked!"
```

A for loop takes three arguments: an initial value (usually a counter), a condition, and a statement that is executed after each iteration of the loop.

```java
String[] names = new String[6];

names[0] = "Jack";
names[1] = "Kate";
names[2] = "James";
names[3] = "Charlie";
names[4] = "John";
names[5] = "Claire";

for (int i = 0; i < names.length; i++) {
	// On the first iteration, i == 0.
	// At the end of each iteration, i is incremented.
	// This will continue as long as i is less than names.length.
	// In other words, this loop will run 6 times. 
	
	println(names[i]);
}

// "Jack"
// "Kate"
// "James"
// "Charlie"
// "John"
// "Claire"
```

# Classes
# Other
# Errors and Exceptions