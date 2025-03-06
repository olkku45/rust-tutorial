# Using Cargo

Cargo is Rust's package manager, and if you're a Linux user, that will be familiar to you, but if you're not, what package managers do is that they
automate the process of installing, upgrading, configuring and removing packages. For smaller projects, using `rustc main.rs` and `./main` is fine, but
if you have something bigger with a lot of files, at that point doing the "rustc" compile command for every file will be tedious. To fix this, we have Cargo.

## Creating a project with Cargo and running it

Start by again typing `cd` followed by the file path of your liking, and typing `cargo new hello_world`. This is the exact same thing we did in the chapter
"Using Rust", and it will create a toml-configuration file and a src-folder containing a Rust file, which has a hello world program inside of it. But what I
didn't mention then, is that it will initialize a Git repository. It won't be initialized however, if you run `cargo new` inside of an existing repository. If you 
don't want to initialize a Git repository, then type `cargo new --vcs=git`. And another thing I didn't mention then, is that you can run a Rust project
with just one command! For this, you'll want to `cd` to the hello_world folder, or whatever you named it, and then type `cargo run`. This will do all the steps
of compiling the files and running the project. You can also do `cargo check` to see whether your project can compile, and doing this periodically
when writing code to see whether the program compiles is very useful in many aspects.

## Why Cargo?

Like I mentioned already, using Cargo helps us with bigger projects, meaning bigger than a few files, and I recommend that you start
using Cargo for every Rust project you're using, even if you're starting a small beginner project, because then you'll get used to using it, and it becomes
second nature when programming in Rust. You'll need Cargo when managing external dependencies, and as the Rust standard library is notoriously small, 
you'll be using it a lot, when you venture out beyond something very small. And from this point onward, I'll assume you're using Cargo, if you're going along
with this tutorial.