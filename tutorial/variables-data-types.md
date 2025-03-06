# Variables and data types

## Variables

In Rust, you initialize variables with either the `let` or `const` keyword. Variables initialized with `let` are immutable by default, however, they
can be changed to be mutable. Variables initialized with `const` on the other hand are *always* immutable, and they can't be changed to be mutable.
Let's now go into what immutable and mutable variables are.

### Immutable variables

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
If you try to run this code, the compiler gives you an error, or maybe before that an extension in your text editor gives you an error,s 
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

### Mutable variables

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
were curious, it is possible to *declare* a variable without *initializing* it, which is the word I've been using here. Let's see what a declared, but not 
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

### Shadowing

## Data types