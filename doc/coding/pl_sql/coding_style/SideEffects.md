[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Avoid side-effects in your programs](../../../../doc/coding/pl_sql/coding_style.md#SideEffects)

Build lots of individual programs, preferably inside packages. Design each program so that it has a single, clearly defined purpose. That purpose should, of course, be expressed in the program's name, as well as in the program header.

Avoid throwing extraneous functionality inside a program. Such statements are called "side-effects" and can cause lots of problems for people using your code.
