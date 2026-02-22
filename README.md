# Self-hosting transpiler
This compiler can transpile itself into a fully functional C program, which in turn can transpile the source code, which in turn can transpile the source code, and so on...
It is implemented in an unnamed esoteric programming language that lacks features such as arithmetic or logical operations as well as functions (however, all of these could be easily emulated by using lists and loops while probably still running faster than their python counterparts).
## Syntax
### Comments
In an esoteric programming language comments are an absolute necessity. Luckily, I recently discovered that this language actually has comments:
```
concat("comment", "This is a comment. It will also execute code at runtime, but usually won't affect your logic")
```
### Control structures
The language has `while` loops and `if` clauses. The condition in `while` loops has to be properly terminated, either with closing brackets or semicolons:
```
var to_be_printed = ["Hello", "World"];
while to_be_printed != [];;
    var next_message : remaining_messages = to_be_printed;;
    to_be_printed = remaining_messages;;
    print(next_message)
endwhile
```
A `while` loop itself can be terminated using `endwhile`.
The condition of an `if` clause is terminated by the keyword `then`, no matter how many semicolons it would otherwise need:
```
if a != b then
    print "unequal";
elseif a == b then
    print "equal";
else
    print "this path is unreachable";
endif
```
An `if` clause itself can be terminated by the keyword `endif` or by multiple semicolons, in case you hate yourself.
### Variables
Variables have no typechecking at all. They can be either an integer, or a list of values. They can be declared using the keyword `var`:
```
var my_integer = 42;
```
They can also be declared in a list-destructuring way, meaning that the first variable is the first element of a list and the second variable is the remainder of said list. This is the only way of accessing list elements:
```
var this_should_be_one : this_should_be_a_list_containing_two_and_three = [1, 2, 3];
```
The value of an already declared variable can be changed using the `=` operator:
```
my_var = 42;
```
All of these operations can also be done using a function-call-like syntax, but I'm not telling you how, in order to keep your code readable.
You can access a variable's name by simply typing it's name. In that case the variable name has to be terminated by a semicolon, comma, or `()` if you're a madman:
```
my_var = my_other_var;;
```
### Functions
There are exactly three built-in functions (if you don't count while which adheres to the same syntax): `concat`, `fload`, and `print`.
You can call them using either parentheses:
```
var result = concat("This", " actually looks pretty normal");
```
or using semicolons:
```
var semicolons = " semicolons.";
print concat "Normally, it is a pretty good idea not to use" semicolons;;;
```
You can even mix both syntaxes if you really want to. But it will probably not make your code more readable.
### Literals
There are three types of literals:
- Integer literals, e. g. `42`
- String literals, e. g. `"Hello, world!"`
- List listerals, e. g. `[["string"], some_variable, 666]`
### Comparisons
Values can be compared for equality using `==`:
```
while a == 42;
    ...
endwhile
```
or inequality:
```
while a != 42;
    ...
endwhile
```
Both operators have to be terminated by a semicolon.
## Workarounds for missing features
The most commonly needed features are AND and OR operations.
You can easily emulate AND by nesting if statements:
```
    if condition_a then
        if condition_b then
            ...
        endif
    endif
```
For OR, you can define an auxiliary variable:
```
    var auxvar = 0;
    if condition_a then
        auxvar = 1;
    elseif condition_b then
        auxvar = 1;
    endif
    if auxvar == then
        ...
    endif
```
Functions can be emulated by simulating a call stack using lists, and numbers can be emulated by lists of digits. However, this isn't needed for the compiler itself.
## Build instructions
Compile the file generated.c first. Then use it to generate a new C source file by redirecting the compiled program's output into the given C source file. Then compile the newly generated C source file using a C compiler.

