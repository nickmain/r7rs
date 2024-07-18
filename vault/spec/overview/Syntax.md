See also [[Formal Syntax]].

Scheme, like most dialects of Lisp, employs a fully parenthesized prefix notation for programs and other data; the grammar of Scheme generates a sublanguage of the language used for data. An important consequence of this simple, uniform representation is that Scheme programs and data can easily be treated uniformly by other Scheme programs. For example, the eval procedure evaluates a Scheme program expressed as data.

The [[read|read]] procedure performs syntactic as well as lexical decomposition of the data it reads. The [[read|read]] procedure parses its input as data (see [[External Representations]]), not as program.
