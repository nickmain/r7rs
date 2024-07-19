A ⟨transformer spec⟩ has one of the following forms:

``` scheme
(syntax-rules (⟨pattern literal⟩ ...) 
	syntax ⟨syntax rule⟩ ...) 
  
(syntax-rules ⟨ellipsis⟩ (⟨pattern literal⟩ ...) 
	syntax ⟨syntax rule⟩ ...)
```

It is an error if any of the ⟨pattern literal⟩s, or the ⟨ellipsis⟩ in the second form, is not an identifier. It is also an error if ⟨syntax rule⟩ is not of the form

* `(⟨pattern⟩ ⟨template⟩)`

The ⟨pattern⟩ in a ⟨syntax rule⟩ is a list ⟨pattern⟩ whose first element is an identifier.

A ⟨pattern⟩ is either an identifier, a constant, or one of the following

``` scheme
(⟨pattern⟩ ...) 
(⟨pattern⟩ ⟨pattern⟩ ... . ⟨pattern⟩)
(⟨pattern⟩ ... ⟨pattern⟩ ⟨ellipsis⟩ ⟨pattern⟩ ...) 
(⟨pattern⟩ ... ⟨pattern⟩ ⟨ellipsis⟩ ⟨pattern⟩ ... . ⟨pattern⟩) 
#(⟨pattern⟩ ...) 
#(⟨pattern⟩ ... ⟨pattern⟩ ⟨ellipsis⟩ ⟨pattern⟩ ...)
```

and a ⟨template⟩ is either an identifier, a constant, or one of the following

``` scheme
(⟨element⟩ ...) 
(⟨element⟩ ⟨element⟩ ... . ⟨template⟩) 
(⟨ellipsis⟩ ⟨template⟩) 
#(⟨element⟩ ...)
```

where an ⟨element⟩ is a ⟨template⟩ optionally followed by an ⟨ellipsis⟩. An ⟨ellipsis⟩ is the identifier specified in the second form of `syntax-rules`, or the default identifier `...` (three consecutive periods) otherwise.

***Semantics***: An instance of `syntax-rules` produces a new macro transformer by specifying a sequence of hygienic rewrite rules. A use of a macro whose keyword is associated with a transformer specified by `syntax-rules` is matched against the patterns contained in the ⟨syntax rule⟩s, beginning with the leftmost ⟨syntax rule⟩. 

When a match is found, the macro use is transcribed hygienically according to the template.



#todo 
