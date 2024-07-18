## Lexical

An identifier is any sequence of letters, digits, and “extended identifier characters”, provided that it does not have a prefix which is a valid number. 
However, the `.` token (a single period) used in the list syntax is not an identifier. 

All implementations of Scheme must support the following extended identifier characters: 

``` scheme
! $ % & * + - . / : < = > ? @ ^ _ ~
```

Alternatively, an identifier can be represented by a sequence of zero or more characters enclosed within vertical lines (`|`), analogous to string literals. Any character, including whitespace characters, but excluding the backslash and vertical line characters, can appear verbatim in such an identifier. In addition, characters can be specified using either an ⟨*inline hex escape*⟩ or the same escapes available in strings.

For example, the identifier `|H\x65;llo|` is the same identifier as `Hello`, and in an implementation that supports the appropriate Unicode character the identifier `|\x3BB;|` is the same as the identifier `λ`. What is more, `|\t\t|` and `|\x9;\x9;|` are the same. Note that `||` is a valid identifier that is different from any other identifier.

``` scheme
...                     + 
+soup+                  <=? 
->string                a34kTMNs 
lambda                  list->vector 
q                       V17a 
|two words|             |two\x20;words| 
the-word-recursion-has-many-meanings
```

See section [[Lexical Structure]] for the formal syntax of identifiers.

## Uses

Identifiers have two uses within Scheme programs:

* Any identifier can be used as a variable or as a syntactic keyword (see [[Variables, Syntactic Keywords, and Regions]] and [[Macros]]).
* When an identifier appears as a literal or within a literal (see [[Literal Expressions]]), it is being used to denote a symbol (see [[Symbols]]).

## Case Sensitivity

In contrast with earlier versions of the Scheme language, the syntax distinguishes between upper and lower case in identifiers and in characters specified using their names. However, it does not distinguish between upper and lower case in numbers, nor in ⟨*inline hex escapes*⟩ used in the syntax of identifiers, characters, or strings. None of the identifiers defined in this report contain upper-case characters, even when they appear to do so as a result of the English-language convention of capitalizing the first word of a sentence.

The following directives give explicit control over case folding:

``` scheme
#!fold-case 
#!no-fold-case
```

These directives can appear anywhere comments are permitted (see section 2.2) but must be followed by a delimiter. They are treated as comments, except that they affect the reading of subsequent data from the same port. 

The `#!fold-case` directive causes subsequent identifiers and character names to be case-folded as if by `string-foldcase` (see [[String Procedures]]). It has no effect on character literals. 

The `#!no-fold-case` directive causes a return to the default, non-folding behavior.