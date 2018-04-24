[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Include standardized modules in packages to dump package state when errors occur](../../../../doc/coding/pl_sql/coding_style.md#DumpErrors)

When an error occurs in one of your PL/SQL blocks, it's often useful to determine the values of persistent package variables at the time of the failure. You can do this to some extent with the debuggers available with many IDEs. That approach doesn't, however, give you access to the data values within a user's application session.

One way to obtain this information is to write a "dump" procedure in each of your packages. This dump procedure displays or records the contents of any relevant variables or data structures - whatever you determine is of value inside that package. You can then feed this information to an error handler, to provide as much information as possible to the person debugging your code.

Providing such dump procedures can dramatically reduce the time spent inserting debug messages only to be removed later, as well as to record problems that appear intermittently, and are hard to reproduce.

This approach obviously relies on the conformance to standards established in advance, so that method names and stack formats can be interpreted, but all of these details can be hidden from view in a package.
