# Myrddin By Example

These are programming examples in the spirit of [gobyexample](https://github.com/mmcgrana/gobyexample), but targeted to the Myrddin programming language.

Myrddin is available at <https://myrlang.org>.

The compiler source is available at <https://github.com/oridb/mc>.

Examples will, if they reference lines in source within an explanation, utilize a plumbable string in the form `foo.myr:3,5` indicating the file `foo.myr` on the line range [3,5], as per [plumb(1)](http://man.cat-v.org/9front/1/plumb).

Examples were composed in acme(1) which allows you to right click these strings to jump to the relevant source lines.

If you'd like to try Myrddin without installing: <https://myrlang.org/playground>

The `;` rune indicates a command to be run from a shell.

A more accurate and narrative-driven tutorial by the language author: <https://myrlang.org/tutorial>

Everything asserted as a fact should be taken with a grain of salt and considered conjecture by a non-expert on the language. No warranty ☺.

## Building

If a given example provides a `bld.proj` file, you can:

	; mbld
	# Produces obj/$binfile
	; ./obj/$binfile
	# Where $binfile is the binary file name produced by mbld

Otherwise, there will only be one file, a Myrddin source file which can be built and run with:

	; mbld -R file.myr

## Index

### Core language functionality

- [Hello World](./HelloWorld)

### Standard library modules

- [Command-Line Arguments](./Args-L)

## References

- <https://myrlang.org/doc/>
- <https://myrlang.org/mbld/>

