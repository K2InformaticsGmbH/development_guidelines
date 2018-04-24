[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Separate package specifications and bodies into different source code files](../../../../doc/coding/pl_sql/coding_style.md#SeparateSpecBody)

Don't combine the specification and body of a package in the same file. Instead, store them in their own files and then, in your installation script for your product, compile all specifications first, followed by the package bodies. By taking this approach, you will find it easier to install and maintain your code base.

Over time, it's likely that your package specification will stabilize, and most changes will take place in the package body. All references to elements in a package are resolved with the specification. If the specification is recompiled, all dependent objects are marked INVALID and must be recompiled. By putting the body in its own file, you can change and recompile it without affecting the status of any other programs.
