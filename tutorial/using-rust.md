# Using Rust

<p>We'll look at writing Rust in an IDE or your preferred code editor, whatever it is, though I'm not going to go over how to setup Rust for proper use
in every code editor there is, instead I will leave it for you to do. I'm personally using Neovim, and I have my configuration file configured for Rust. 
Rust can't be run straight from the code editor though, unless you are using something like VS Code that has an extension for good Rust support, 
instead Rust code will have to be run from the terminal. If that is scary to you, well, you will just have to get used to it.<p>

## cd: into your desired directory

Hopefully you have installed Rust by now. So first, use `cd` followed by the desired directory path to navigate into that directory, which will be the place where our Rust files will
show up, yes, there will be many files.

![Make directory and cd](https://github.com/olkku45/rust-tutorial/blob/main/images/mkdir-cd-rust-tutorial.png)

## Your first Rust program created automatically

If you want to make your first "Hello world!" program in Rust automatically using commands, follow this part, but if you want to
do it manually, skip to the next part where we do that. 
When we've ensured that we're in the directory that we want to be in, you type the following into the terminal: 
`cargo new  NAME-HERE` where you replace NAME-HERE with the name that you want for the automatically created folder. For example,
we can say `cargo new hello_world`. This will create a folder called hello_world containing a "src" folder, which contains our "main.rs" Rust file, and also a
Cargo.toml file. We''ll look at the .toml file later. If you have a look at the main.rs file, you can see that a program that will print "Hello, world!" has
been created! But now, how do we run the code? First, let's save the file just in case, and then type in the terminal, where we're hopefully still
in the same desired directory, `cd NAME-HERE` again replacing NAME-HERE with your folder's name, to navigate to the new folder, and after this type 
`cd src`, because we weren't where we actually needed to be yet, then `rustc main.rs`, and finally `./main`. Now we've printed
"Hello, world!" inside the terminal, if you followed the steps correctly and the steps were clear enough! Let's say we want to print "My name is
NAME", where you replace NAME with your own name, well, you can just edit whatever is inside the quotes inside the println!-macro in the main.rs-file,
and do `./main` again. Lets do that, and... what? Why did that not change anything? It's because we need to type `rustc main.rs`
again to tell the Rust compiler to make the changes, and then we can do `./main`. Also, don't forget to save the changes you made
inside the text editor you're using before you do these two steps! 

## Your first Rust program created manually

When we've ensured we're in the directory we want to be in, type the following into the terminal: `touch main.rs` to create an empty Rust source file. 
Now open it in your text editor of choice. For example, I'm using Neovim, so I type `nvim main.rs` into the terminal, but that will look 
different for you depending on the text editor you're using. The difference here compared to the "automatic" method is that we don't get a .toml
file and a folder containing a source Rust file. We'll go into what a .toml file is in the next part, don't worry. Now, when the file is opened, we can get
our hands dirty actually doing something (albeit very very small). First, we have to create a main function that our program runs inside of. We'll go into why this is
in another chapter. It looks like this:
```
fn main() {
	
}
```
	
Now, to make our "Hello, world!" print, type:
```	
fn main() {
	println!("Hello, world!");
}
```
	
This should work. Now to run the code, what we have to do, is go in the terminal where you possibly still are cd:d into the directory where the 
main.rs file resides, but if you aren't, you will have to do that now, but when you are, you will run `rustc main.rs` and `./main`. Now "Hello, world!"
should be printed to your terminal! If you want to change what the program prints, you can do that by changing whatever is inside of the quotes
in the println! macro (we'll go into what macros are in another chapter), and doing `rustc main.rs` and `./main` again. You have to do `rustc main.rs` again
basically to tell the Rust compiler to make the changes, and `./main` is for running the code.
	
<p> Now you should have Rust installed, and you should be able to run stuff with it.<p>