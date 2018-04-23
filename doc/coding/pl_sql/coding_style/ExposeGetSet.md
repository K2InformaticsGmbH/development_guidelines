[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Expose package globals using "get and set" modules](../../../../doc/coding/pl_sql/coding_style.md#ExposeGetSet)

Data structures (scalar variables, collections, cursors) declared in the package specification (not within any specific program) are directly referenceable from any program run from a session with `EXECUTE` authority on the package. This is always a bad idea and should be avoided.

Instead, declare all package-level data in the package body and provide "get and set" programs - a function to `GET` the value and a procedure to `SET` the value - in the package specification. Developers can then access the data through these programs, and automatically follow whatever rules you establish for manipulating that data.
