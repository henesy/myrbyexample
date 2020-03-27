# Command-Line Arguments

Myrddin has support in the standard library for command-line argument parsing.

## Source

### args.myr:11,18

	cmd = std.optparse(args, &[
		.argdesc = "words…",
		.opts = [
			[.opt='r',						.desc = "reverse output"],
			[.opt='m',	.arg = "mark",		.desc = "list items with prefix 'mark'"],
			[.opt='T',	.arg = "period",	.desc = "set print sleep delay to 'period' ms"],
		][:]
	])

The `cmd` variable is assigned a `std.optparsed` type struct via the `std.optparse()` function.

The definitions provided in this block will be used for flag parsing later and for formatting the usage message provided by the library-provided `-h` and `-?` flags.

This usage will look like:

	usage: ./out [-h?r] [-m mark] [-T period] words…
		-h	print this help message
		-?	print this help message
		-r	reverse output
		-m mark	list items with prefix 'mark'
		-T period	set print sleep delay to 'period' ms

### args.myr:20,25

	for opt : cmd.opts
		match opt
		| ('r', ""):
			reverse = true
		| ('m', arg):
			mark = arg

This section shows the beginning of the iteration, in order, of the flag (option) arguments to the program.

Each argument is matched against for parsing.

The `r` flag does not take an argument as indicated by the `""` in the match case.

The `m` flag takes an argument as indicated by the presence of the name `arg` in the match case.

### args.myr:26,32

	| ('T', arg):
			match std.intparse(arg)
			| `std.Some v:
				delay = v * std.Msec
			| `std.None:
				std.fatal("err: invalid argument for period\n")
			;;

A byte slice argument is parsed into a number and assigned to a pre-existing variable.

### args.myr:38,46

This section reverses, in-place, the `cmd.args` slice.

The `cmd.args` slice is the set of arguments which were not consumed by the preceding flag-type arguments.

### args.myr:48,51

This section prints a mark and argument from the `cmd.args` slice, in order, sleeping for a given period `delay` after each print.

## Demo

	; mbld -b out args.myr && ./out -h && ./out -r -m '«' -T 500 -- -ß A b C d E

	<out -h && ./out -r -m '«' -T 500 -- -ß A b C d E
	usage: ./out [-h?r] [-m mark] [-T period] words…
		-h	print this help message
		-?	print this help message
		-r	reverse output
		-m mark	list items with prefix 'mark'
		-T period	set print sleep delay to 'period' ms
	« E
	« d
	« C
	« b
	« A
	« -ß
	;

## References

- https://myrlang.org/doc/libstd/cli
