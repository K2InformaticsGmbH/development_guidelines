[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Group related data structures and functionality together in a single package](../../../../doc/coding/pl_sql/coding_style.md#GroupRelated)

Even if you don't take advantage of features unique to packages, such as persistent data, you can still use packages to organize—and store together—related code and data structures.

Without packages, you might end up with several hundred standalone procedures and functions and many repeated cursor, `TYPE`, and variable declarations.

A package gives a name to a set of program elements: procedures, functions, userdefined types, variable and constant declarations, cursors, and so on. By creating a package for each distinct area of functionality, you create intuitive containers for that functionality
