[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Never return `NULL` from Boolean functions](../../../../doc/coding/pl_sql/coding_style.md#NeverNull)

A Boolean function should return only `TRUE` or `FALSE`. If a Boolean function returns a `NULL`, how should the user of that function interpret and respond to that value? Does it indicate you passed in invalid data? Should it be considered `TRUE` or `FALSE`? Or should the developer test explicitly for `NULL`? Well, we should do explicit tests for `NULL` if we are uncertain about the function's behavior, but we rarely remember to do so or feel it's necessary to make the effort. Instead, we check for `TRUE` or `FALSE` and thus allow bugs to creep into our code.

If the Boolean function can return `NULL`, you probably need to look at the implementation of the function to determine the action to take on a `NULL` return value. Yet you will not always be able to (or want to) look at the function's body.

A non-Boolean function can use a `NULL` return value to indicate failure. A function that returns the title of a book for an ISBN number returns NULL for an invalid ISBN. That makes sense. On the other hand, a function that tells you whether or not a book is in print doesn't help you much if it returns `NULL`.
