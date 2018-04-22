[Development Guidelines](../../../README.md) / [Coding](../../../README.md#coding) / [PL/SQL](../../../README.md#coding_pl_sql) / [Coding Style](Coding Style)

## [Tag module `END` statements with module names](../../../../Coding_Style.md#TagEnd)

Every program has an `END` statement. You can, and should, append the name of the program to the end statement:

```pl/sql
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
