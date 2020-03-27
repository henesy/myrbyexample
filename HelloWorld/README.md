# Hello World

This program prints the classic hello world message.

## Source

### hello.myr:1

	use std

The `use` keyword imports a library into the current namespace for calling/use.

### hello.myr:3

	const main = {

The `const` keyword indicates a constant (immutable) value.

The name `main` is assigned to the value.

The `{` rune begins a function literal declaration.

Note the omission of a type for the name `main`. Explicit types in declaration may be omitted and are inferred if they are omitted as such using contextual information within the source such as the type of a literal assignment, etc.

This line could also be written equivocally as:

	const main = {;

The `;` rune in this case is semantically the same as the `\n` in the function literal declaration, signifying the omission of any arguments to the function.

See [Functions](../Functions) for more details on functions.

### hello.myr:4

	std.put("Hello World! ☺\n")

The `std.put` name calls the function named `put` in the library `std` as per the `use` keyword above.

The parentheses indicate the calling of a function.

The double quotes indicate a string literal declaration.

All strings in Myrddin are conventionally utf-8 encoded strings. Note the `☺` rune included in the string.

### hello.myr:5

	}

The `}` rune ends a function literal declaration.

## Demo

	; mbld -R hello.myr
	Hello World! ☺
	;

## Exercises

- Try making the hello world example as line-compact as possible

