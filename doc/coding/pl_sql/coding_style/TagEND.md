[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Tag module `END` statements with module names](../../../../doc/coding/pl_sql/coding_style.md#TagEnd)

Every program has an `END` statement. Append the name of the program to the end statement:

```PLSQL
CREATE OR REPLACE PACKAGE BODY <pkgname>
IS
    FUNCTION <funcname> (...)
        RETURN BOOLEAN
    IS
        ...
    BEGIN
        ...
    END <funcname>;

PROCEDURE <procname> (...)
    IS
        ...
    BEGIN
        ...
    END <procname>;
END <pkgname>;
```
