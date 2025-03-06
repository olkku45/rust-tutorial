# Using Rust

<p>We'll look at writing Rust in an IDE or your preferred code editor, whatever it is, though I'm not going to go over how to setup Rust for proper use
in every code editor there is, instead I will leave it for you to do. I'm personally using Neovim, and I have my configuration file configured for Rust. 
Rust can't be run straight from the code editor though, unless you are using something like VS Code that has an extension for good Rust support, 
instead Rust code will have to be run from the terminal. If that is scary to you, well, you will just have to get used to it.<p>

## cd: into your desired directory

Hopefully you have installed Rust by now. So first, use `cd` followed by the desired directory path to navigate into that directory, which will be the place where our Rust files will
show up, yes, there will be many files.

![Make directory and cd](https://github.com/olkku45/rust-tutorial/blob/main/images/mkdir-cd-rust-tutorial.png)

## Your first Rust program

When we've ensured that we're in the directory that we want to be in, you type the following into the terminal: 
`cargo new  NAME-HERE` where you replace NAME-HERE with the name that you want for the automatically created folder. For example,
we can say `cargo new hello_world`. This will create a folder called hello_world containing a "src" folder, which contains our "main.rs" Rust file, and also a
Cargo.toml file. We''ll look at the .toml file later. If you have a look at the main.rs file, you can see that a program that will print "Hello, world!" has
been created! But now, how do we run the code? First, let's save the file just in case, and then type in the terminal, where we're hopefully still
in the same desired directory, `cd NAME-HERE` again replacing NAME-HERE with your folder's name, to navigate to the new folder, and after this type 
`cd src`, because we weren't where we actually needed to be yet, then `rustc main.rs`, and finally `./main`. Now we've printed
"Hello, world!" inside the terminal, if you followed the steps correctly and the steps were clear enough! Let's say we want to print "My name is
NAME", where you replace NAME with your own name, well, you can just edit whatever is inside the quotes inside the println!-function in the main.rs-file,
and do `./main` again. Lets do that, and... what? Why did that not change anything? It's because we need to type `rustc main.rs`
again to tell the Rust compiler to make the changes, and then we can do `./main`. Also, don't forget to save the changes you made
inside the text editor you're using before you do these two steps!
<p> Now you should have Rust installed, and you should be able to run stuff with it.<p>