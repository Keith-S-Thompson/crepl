`crepl` is a simple
[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)
(read-eval-print loop) for C, implemented in Perl.

## Usage:

Enter a single line of C code.  It will be wrapped in a simple
C program, compiled, and executed if compilation was successful.

Type `h`, `help`, or `?` for a usage message.

The generated program, by default, is:

    #include <stdio.h>
    int main(void) {
        /* YOUR LINE HERE */
        ;
    }

The added `;` lets you omit the trailing semicolon on the entered statement.

`crepl` uses Perl's
[`Term::ReadLine`](https://metacpan.org/pod/Term::ReadLine) module,
so it supports line editing.

By default, the C program has `#include <stdio.h>` at the top.
More headers can be added to the list with `include` command:

    {} include <stdlib.h>

Adding `<math.h>` or `<tgmath.h>` adds `-lm` to the compiler command
line.

Type `include` by itself to list the current include list.

Multiple input lines are not combined; the body of the C program
is just the one line you entered.  Of course you can enter multiple
statements on a single line.  No state is kept from one line to the
next, other than the list of included headers.

The C program is compiled with `gcc -std=c11 -pedantic-errors`.
