By convention, `?` is the final character of the names of procedures that always return a boolean value. Such procedures are called predicates. Predicates are generally understood to be side-effect free, except that they may raise an exception when passed the wrong type of argument. 

Similarly, `!` is the final character of the names of procedures that store values into previously allocated locations (see [[Storage Model]]). Such procedures are called mutation procedures. The value returned by a mutation procedure is unspecified. 

By convention, `->` appears within the names of procedures that take an object of one type and return an analogous object of another type. For example, `list->vector` takes a list and returns a vector whose elements are the same as those of the list. 

A *command* is a procedure that does not return useful values to its continuation. 

A *thunk* is a procedure that does not accept arguments.