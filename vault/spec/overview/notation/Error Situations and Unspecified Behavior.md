
When speaking of an error situation, this report uses the phrase “an error is signaled” to indicate that implementations must detect and report the error. An error is signaled by raising a non-continuable exception, as if by the procedure [[Raise|raise]]. The object raised is implementation-dependent and need not be distinct from objects previously used for the same purpose. In addition to errors signaled in situations described in this report, programmers can signal their own errors and handle signaled errors.

The phrase “an error that satisfies *predicate* is signaled” means that an error is signaled as above. Furthermore, if the object that is signaled is passed to the specified predicate (such as `file-error?` or `read-error?`), the predicate returns `#t`.

If such wording does not appear in the discussion of an error, then implementations are not required to detect or report the error, though they are encouraged to do so. Such a situation is sometimes, but not always, referred to with the phrase “an error.” In such a situation, an implementation may or may not signal an error; if it does signal an error, the object that is signaled may or may not satisfy the predicates `error-object?`, `file-error?`, or `read-error?`. Alternatively, implementations may provide non-portable extensions.

For example, it is an error for a procedure to be passed an argument of a type that the procedure is not explicitly specified to handle, even though such domain errors are seldom mentioned in this report. Implementations may signal an error, extend a procedure’s domain of definition to include such arguments, or fail catastrophically.

This report uses the phrase “may report a violation of an implementation restriction” to indicate circumstances under which an implementation is permitted to report that it is unable to continue execution of a correct program because of some restriction imposed by the implementation. Implementation restrictions are discouraged, but implementations are encouraged to report violations of implementation restrictions.

For example, an implementation may report a violation of an implementation restriction if it does not have enough storage to run a program, or if an arithmetic operation would produce an exact number that is too large for the implementation to represent.

If the value of an expression is said to be “unspecified,” then the expression must evaluate to some object without signaling an error, but the value depends on the implementation; this report explicitly does not say what value is returned.

Finally, the words and phrases “must,” “must not,” “shall,” “shall not,” “should,” “should not,” “may,” “required,” “recommended,” and “optional,” although not capitalized in this report, are to be interpreted as described in [[RFC 2119]]. They are used only with reference to implementer or implementation behavior, not with reference to programmer or program behavior.