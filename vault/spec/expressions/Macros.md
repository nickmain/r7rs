
* [[Binding Constructs for Syntactic Keywords]]
* [[Pattern Language]]
* [[Signaling Errors in Macro Transformers]]

---

Scheme programs can define and use new derived expression types, called *macros*. Program-defined expression types have the syntax

- `(⟨keyword⟩ ⟨datum⟩ ...)`

where ⟨keyword⟩ is an identifier that uniquely determines the expression type. This identifier is called the *syntactic keyword*, or simply *keyword*, of the macro. The number of the ⟨datum⟩s, and their syntax, depends on the expression type.

Each instance of a macro is called a *use* of the macro. The set of rules that specifies how a use of a macro is transcribed into a more primitive expression is called the *transformer* of the macro.

The macro definition facility consists of two parts:  

* A set of expressions used to establish that certain identifiers are macro keywords, associate them with macro transformers, and control the scope within which a macro is defined, and 
* a pattern language for specifying macro transformers.

The syntactic keyword of a macro can shadow variable bindings, and local variable bindings can shadow syntactic bindings. Two mechanisms are provided to prevent unintended conflicts:

* If a macro transformer inserts a binding for an identifier (variable or keyword), the identifier will in effect be renamed throughout its scope to avoid conflicts with other identifiers. Note that a global variable definition may or may not introduce a binding; see [[Variable Definitions]].
* If a macro transformer inserts a free reference to an identifier, the reference refers to the binding that was visible where the transformer was specified, regardless of any local bindings that surround the use of the macro.

In consequence, all macros defined using the pattern language are “hygienic” and “referentially transparent” and thus preserve Scheme’s lexical scoping.

Implementations may provide macro facilities of other types.