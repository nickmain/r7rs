Every identifier defined in this report appears in one or more of several *libraries*. 

Identifiers defined in the *base library* are not marked specially in the body of the report. This library includes the core syntax of Scheme and generally useful procedures that manipulate data. For example, the variable `abs` is bound to a procedure of one argument that computes the absolute value of a number, and the variable `+` is bound to a procedure that computes sums. 

The full list of all the standard libraries and the identifiers they export is given in [[Standard Libraries]].

---
All implementations of Scheme:

* Must provide the base library and all the identifiers exported from it. 
* May provide or omit the other libraries given in this report, but each library must either be provided in its entirety, exporting no additional identifiers, or else omitted altogether. 
* May provide other libraries not described in this report. 
* May also extend the function of any identifier in this report, provided the extensions are not in conflict with the language reported here. 
* Must support portable code by providing a mode of operation in which the lexical syntax does not conflict with the lexical syntax described in this report.
