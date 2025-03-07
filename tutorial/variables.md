# Variables
In Rust, you declare variables with either the `let` or `const` keyword. Variables declared with `let` are immutable by default, however, they
can be changed to be mutable. Variables declared with `const` on the other hand are *always* immutable, and they can't be changed to be mutable.
Let's now go into what immutable and mutable variables are.

## Immutable variables

Variables in Rust are immutable by default, meaning when you initialize a variable with the `let` keyword, for example here:
```rust
fn main() {
    let number = 100;
    println!("{number}");
}
```
you can't change the variable's value without the Rust compiler complaining:
```rust
fn main() {
    let number = 100;
    println!("{number}")
    number = 101;  // here's where it goes wrong
    println!("{number}")
}
```
If you try to run this code, the compiler gives you an error, or maybe before that an extension in your text editor gives you an error, 
which says something like: 
```rust
number = 101;
^^^^^^^^^^^^ cannot assign twice to immutable variable
```
This is one of the most basic errors we have in Rust, and the reason we get it here is that an immutable variable's value cannot be changed 
after its initialization. If you initialize a variable with `const`, the value stays truly constant, like think of the speed of light, it can't change no matter what.
If you try to do the same thing with `const`, you get the same error:
```rust 
fn main() {
    const number = 100;
    println!("{number}");
    number = 101;
    println!("{number}")
}
```
Except we actually don't since we have to specify the data type of the variable when using `const`! We'll go into data types later in this chapter, but
let's say `number` is a 32-bit integer:
```rust 
fn main() {
    const number: i32 = 100;  // i32 = 32-bit integer
    println!("{number}");
    number = 101;
    println!("{number}")
}
```
And now we get... a different error, hopefully, which says we can't assign 101 to "number", a constant variable which cannot be changed. Let's remove
the reassignment and the second print statement, and we'll let the compiler be happy:
```rust 
fn main() {
    const number: i32 = 100;
    println!("{number}");
}
```
At this point though, you might get a warning saying "constant 'number' should have an upper case name", which is just due to Rust's naming conventions,
where the names of constants should be upper case. You can name them however you want for now, though it would be good to start using the naming conventions
of the language early to get used to them and to not have to think about them later on, so you can change "number" to "NUMBER", however odd it may seem.

## Mutable variables

So, to change a variable initialized by `let`, we add `mut` after it:
```rust
fn main() {
    let mut number = 100;
    println!("{number}")
    number = 101;
    println!("{number}")
}
```
The compiler will accept this, so we have done something correctly! When you initialize a variable with `let mut`, you will be able to modify its value later 
on in the program. However, if you try this:
```rust
fn main() {
    const mut number: i32 = 100;
    println!("{number}")
    number = 101;
    println!("{number}")
}
```
You will get an error that says "const globals cannot be mutable", so yeah, you just can't change constants, they're *always* immutable. A side note if you 
were curious, it is possible to *declare* a variable without *initializing* it. Let's see what a declared, but not 
initialized variable looks like:
```rust
fn main() {
    let x: i32; 
}
```
Yes, you can specify types for variables that have been declared with `let`, and you often do that. Why we don't necessarily need to do that though is due to
Rust's type inference system, which basically infers from context what type a variable is. If we do "let x = 45", Rust infers here that x is an i32.
But as you saw before, type inference doesn't apply to constants.  Anyways, variables declared with `const` must be initialized, so you need to 
assign a value to it immediately, or the compiler won't be happy, and variables declared with `let` can be uninitialized at first, but they do need to be
initialized before use, so you can't do:
```rust
fn main() {
    let x: i32; 
	println!("{x}")
	x = 100
}
```
Or else you'll get an error saying that the variable is "possibly uninitialized", which we here do know that it definitely is.	

### Shadowing variables

It is possible to declare a new variable with the same name as a previous variable. This is called *shadowing*, since the old variable gets "overshadowed", or 
rather, the first variable gets *shadowed* by the second one. You can only shadow a variable with `let` and not `const`. An example of shadowing is:
```rust
fn main() {
    let const = 3.14
	let const = const - 1
}
```
Except this gives us an error, because we can't use keywords as variable names, or more generally, we can't use keywords as names for anything in Rust,
much like in Python as well. Also, here Rust infers that the number is a float. But let's do it correctly:
```rust
fn main() {
    let number= 3.14
	let number = number - 1
}
```
Except that here we get an error as well, which says something like "cannot subtract integer from float", so with operations, the types of values
need to be the same. We'll get more into this in the data types-section. Let's correct that:
```rust
fn main() {
    let number= 3.14
	let number = number - 1.0
}
```
And now the compiler is happy. You do see that the compiler gives us a lot of errors, which is good actually. We'll go more into the compiler in its chapter.
So, we have shadowed the variable "number" here with a new variable "number", and when the program runs, the compiler chooses the *shadowing* variable
to be used, so "let number = number - 1.0" here. Additionally, you can't do the following:
```rust
fn main() {
    let number= 3.14
	number = number - 1.0
	println!("{number}")  // prints 2.14
}
```
Because here we're assigning twice to an immutable variable, as the error says. So, shadowing is basically just re-declaring a variable with the same name using `let`.

## Mutation

Now, let's also talk about mutation while we're talking about shadowing, since mutation is very similar. In effect, mutation means changing the value of a *mutable* variable
without re-declaring it using `let` again. Let's see that in action:
```rust
fn main() {
    let mut number = 3.14
	number -= 1.0
	println!("{number}")  // prints 2.14
}
```
So, this does not create a new variable, it only mutates, so changes the existing one's value. It also preserves the type of the value, and you cannot change the
type of the variable when mutating it. You can, however, change the type of a variable when shadowing it, which can be very useful in certain situations.
The reason for this is that with mutation, you're not declaring the variable again, and you can only choose a variable's type when you declare it. Also,
you can't do:
```rust
fn main() {
    let number = 3.14
	let number += 1
}
```
So you can't declare a variable when you're mutating it. 

## Shadowing versus mutation

Questions you might have right now are when should you use mutations versus when should you use shadowing? 
The answer is that when you want to change the type of a variable, or you want to keep variables immutable after modifying them, for example, when
you don't want later parts of your code to accidentally modify the value of a variable, use shadowing. Rust also promotes a functional programming style,
which favors immutability, so using shadowing abides by this.
If you need to modify a variable multiple times, e.g. in a loop, or you want to avoid unnecessary memory allocation, use mutation. 

