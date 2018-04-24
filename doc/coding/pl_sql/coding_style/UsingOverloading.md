[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Simplify and encourage module usage using overloading to widen calling options](../../../../doc/coding/pl_sql/coding_style.md#UsingOverloading)

Overloading (also known as static polymorphism in the world of object-oriented languages) is the ability to create two or more programs with the same name. While you can do this in the declaration section of any PL/SQL block, it's most useful and common in package specifications.

The primary reason to overload programs in your package is to transfer the "need to know" about how to use your functionality from the user to the package itself. You anticipate the different ways that developers will want to use the packaged feature and then offer matching variations of the "same" program.
