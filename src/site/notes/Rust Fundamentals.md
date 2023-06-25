---
{"dg-publish":true,"permalink":"/rust-fundamentals/"}
---

Related: #Rust [[Rust\|Rust]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 22-06-2023
***

- Similar to [[Intro to C++\|C++]]

# Run Your Code

- Files saved with `.rs` extension
- Compile using the **Rust Compiler**

```
rustc hello.rs
```

- This will create a binary file called `hello`
- This can be executed

```
./hello
```

# Functions

- Use `fn` keyword
- Default returns void

```rust
fn main(){ // requires a main fn to run
	// Comments are the same as other languages
	println!("Hello World");
}
```

## Function Parameters

- Bit different, variable name comes **before** the [[Rust DataTypes\|datatype]]

```rust
fn example(num:i32) {}
```

## Return Types

- Also different, the return type is at the end of the function
- Woww they're so quirky

```rust
fn example(num:i32) -> i32 {}
```

# Formatted Print

- Uses **macros** defined in `std::fmt`
- Rust checks formatting correctness at compile time

- format!
	- Write the formatted text to `String`
- print!
	- Same as format! but text is printed to console
	- `io::stdout`
- println!
	- Same as print! but appends a newline
- eprint!
	- Same as print! but printed as error
	- `io::stderr`
- eprintln!
	- Same as eprint! but with a newline

## Examples

```rust
// The `{}` will be automatically replaced with any arguments.
println!("{} days", 31);

// Positional arguments can be used. 
// Arguments start at 0 immediately after the format string.
println!("{0}, this is {1}. {1}, this is {0}", "Alice", "Bob");

// Can also have named arguments
println!("{name} is {age}. {name} is cool.", name="Hamish", age=18);
```

