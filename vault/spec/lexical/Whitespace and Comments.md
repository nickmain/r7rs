 *Whitespace* characters include the space, tab, and newline characters. (Implementations may provide additional whitespace characters such as page break.) 
 
 Whitespace is used for improved readability and as necessary to separate tokens from each other, a token being an indivisible lexical unit such as an identifier or number, but is otherwise insignificant. Whitespace can occur between any two tokens, but not within a token. Whitespace occurring inside a string or inside a symbol delimited by vertical lines is significant.

The lexical syntax includes several comment forms. Comments are treated exactly like whitespace.

A semicolon (`;`) indicates the start of a line comment. The comment continues to the end of the line on which the semicolon appears.

Another way to indicate a comment is to prefix a ⟨*datum*⟩ (cf. [[External Representations]]) with `#;` and optional ⟨*whitespace*⟩. The comment consists of the comment prefix `#;`, the space, and the ⟨*datum*⟩ together. This notation is useful for “commenting out” sections of code.

Block comments are indicated with properly nested `#|` and `|#` pairs.

``` scheme
#|
   The FACT procedure computes the factorial
   of a non-negative integer.
|# 
(define fact 
  (lambda (n) 
    (if (= n 0) 
       #;(= n 1) 
       1   ;Base case: return 1 
       (* n (fact (- n 1))))))
```

