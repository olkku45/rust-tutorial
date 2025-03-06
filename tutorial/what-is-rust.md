# What is Rust?

## Can you tell me already?

<p> Rust is a memory-safe programming language that doesn't have a garbage collector or runtime,
and instead of a garbage collector, it uses a concept called "ownership and borrowing" to keep bugs at bay. Don't worry
if you don't get what I'm saying just yet, we'll go into these concepts. 

## Low-level

<p>The language is general purpose, meaning it's not 
really specialized for one use case, and it's a low-level systems language, much like C and C++. Low-level here means that the language operates "close"
to the computer's components itself, meaning the language has little abstraction (layering) from actual machine instructions. On the other 
hand, a language like Python or Javascript is a high-level language, meaning the language has more abstraction from machine instructions,
and  is also easier to understand and work with than a low-level language. You can think of the higher level of abstraction as 
the depth of knowledge about how computers function that you need for using the language. So in Python, you don't need to worry about
accessing memory, because the language does that for you, meanwhile in a low-level language like C, you do manual memory management, so
you access memory yourself through the code that you write.<p>

## Memory safety

<p>Remember how I said Rust is a memory safe language? Well, C is not considered memory safe, because it doesn't enforce controls over memory access, and it lets you do whatever
you want. But as you have heard a million times, with great power comes great responsibility, and the lack of memory safety with the C 
language can cause people to make dangerous mistakes that can lead to vulnerabilities in software. Rust is a unique language, because 
it's a low-level language that actually enforces rules that restrict your ability to do whatever you want with memory, which makes it 
memory safe. This is the main reason that I now chose to start learning Rust over C, even though some people say you should learn C before Rust,
since understanding how C works would help you tremendously in understanding how Rust works. 
And a side note, Rust and C are not *as* low level as something like assembly or plain binary, which the computer processes
directly, they still do have something between the code written and actual machine instructions.<p>

## Garbage collector and runtime

<p>Now, about the garbage collector. If a programming language has a garbage collector, like Python has, that means that the language does 
memory management for you. The garbage collector's job is to free up memory that has been allocated to objects that are no longer used 
by the program, and this memory is called garbage. Then, the freed up memory can be used again. Rust doesn't have this, and you have to do
memory management by yourself, but in a safe and controlled manner that is enforced upon you, unlike in C, where you just have to have
the pure programming skill to be able to do memory management in a safe manner. Also, about the runtime. High-level languages like
Python have a runtime environment, which is basically the environment in which the program executes in, which includes things like
how the language is compiled,  how it's executed, and how memory is managed.  Rust on the other hand doesn't have a runtime, it
compiles to native code much like C does, and this lack of runtime makes these languages really fast compared to
languages that have runtimes.  Python is an *interpreted* language,
while Rust is *compiled* , also (though technically, Python is also compiled, but don't worry about it). So, another takeaway is that Rust is faster than a high-level
language because of its lack of runtime, and because of this, Rust is very good for programs and software that require high performance, like
operating systems, game engines and CLI (command line) tools. Another thing, because of their lack of runtimes, languages like Rust can
be used to create operating systems, but not something like Python, since you need an operating system for a runtime to work, so in an 
environment where you don't have access to a runtime, you need a language without a runtime.<p>