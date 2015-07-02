# cmdline-calc

Command line calculator. A simple bash wrapper around `bc` for easier use and
nicer output. Accepts and solves a single equation on the command line.

The equation can have intermixed hex and decimal values.


# Usage
```
Usage: calc [OPTION]... [EQUATION]
Solve an equation.
    -d        output in decimal even if EQUATION contains hex numbers
        -h        output in hex even if EQUATION contains decimal numbers
	    --help    display this text and exit

	    EQUATION may contain hex numbers so long as they are preceded by
	    '0x'.
	    If EQUATION contains a hex number, the output will be in hex if -d
	    is not given.
	    See `man bc` for legal EQUATION operators.

	    Default precision is 15 digits. It can be overidden by setting the
	    $PRECISION
	    environment variable.
```


# Examples
```
$ calc 1+1
2
$ calc '(1+1)*2'
4
$ calc 2.2^2
4.84

$ calc 'sqrt(2)'
1.41421356237309
$ PRECISON=25 calc 'sqrt(2)'
1.4142135623730950488016887

$ calc 0xA+0xA
0x14
$ calc -d 0xA+0xA
20
$ calc 0xa+1
0xb
$ calc 0xA+1
0xB
$ calc -d 0xA+1
11
$ calc 0xa+10+0xB+11
0x2A
```


# Dependencies
[`bc`](https://www.gnu.org/software/bc/)
