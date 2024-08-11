# The Java Interpreter

Error codes for system exits are derived from here: [https://man.freebsd.org/](https://man.freebsd.org/cgi/man.cgi?query=sysexits&apropos=0&sektion=0&manpath=FreeBSD+4.3-RELEASE&format=html)

## Lox Main

This runs the system, taking in either a file or an IO stream from the CLI. It runs the Scanner (lexer) and then parses the tokens.

## Scanner/Lexer

This is a fairly self evident class. It has a hash of keywords to check against and a `scanTokens` function that switches over the potential tokens, adding them to a new array list.

## Parser

The parser takes a token list and runs through a recursive expression check. Starting with equality, it recursively goes from top to bottom (in terms of the degree of "nonterminal-ness") of the types of tokens, creating `Expr` expression objects for each type it encounters, adding to the appropriate fields of each expression type.

There are some checks for errors and a synchronization system which checks for errors at various boundaries ("class", "var", "if", etc.) before returning back with an error in order to limit the number of error messages.


