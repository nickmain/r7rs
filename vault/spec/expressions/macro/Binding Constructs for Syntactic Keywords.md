The `let-syntax` and `letrec-syntax` binding constructs are analogous to `let` and `letrec`, but they bind syntactic keywords to macro transformers instead of binding variables to locations that contain values. 

Syntactic keywords can also be bound globally or locally with `define-syntax`; see [[Syntax Definitions]].

#### let-syntax

* `(let-syntax ⟨bindings⟩ ⟨body⟩)`
	- ⟨bindings⟩ has the form
		`((⟨keyword⟩ ⟨transformer spec⟩) ...)`

Each ⟨keyword⟩ is an identifier, each ⟨transformer spec⟩ is an instance of `syntax-rules`, and ⟨body⟩ is a sequence of zero or more definitions followed by one or more expressions. It is an error for a ⟨keyword⟩ to appear more than once in the list of keywords being bound.

*Semantics*: The ⟨body⟩ is expanded in the syntactic environment obtained by extending the syntactic environment of the `let-syntax` expression with macros whose keywords are the ⟨keyword⟩s, bound to the specified transformers. Each binding of a ⟨keyword⟩ has ⟨body⟩ as its region.

``` scheme
(let-syntax ((given-that (syntax-rules () 
			   ((given-that test stmt1 stmt2 ...) 
				(if test 
				   (begin stmt1 
						  stmt2 ...)))))) 
	(let ((if #t)) 
		(given-that if (set! if ’now))
		 if))    ==> now 
		 
(let ((x ’outer)) 
	(let-syntax ((m (syntax-rules () ((m) x)))) 
	(let ((x ’inner)) 
	   (m))))    ==> outer
```

#### letrec-syntax

#todo 