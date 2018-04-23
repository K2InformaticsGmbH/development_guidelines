[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Centralize `TYPE` definitions in package specifications](../../../../doc/coding/pl_sql/coding_style.md#CentralizeTypes.md)

As you use more and more of the PL/SQL language features, you will define many `TYPE`s of things, including:

- `SUBTYPE`s that define application-specific datatypes
-·Collection `TYPE`s, such as lists of numbers, dates, or records
- Referenced cursor `TYPE`s, from which cursor variables are declared

Some of these `TYPE`s can be used unchanged throughout your application; other types are specific to some part of an application but are standard within that.

In either case, create a package to hold these standard `TYPE`s, so that they can be used in multiple programs.

#### Example:

```PLSQL
CREATE OR REPLACE PACKAGE colltype
IS
    TYPE boolean_ntab  IS TABLE OF BOOLEAN;
    TYPE boolean_ibtab IS TABLE OF BOOLEAN INDEX BY BINARY_INTEGER;
    TYPE date_ntab     IS TABLE OF DATE;
    TYPE date_ibtab    IS TABLE OF DATE    INDEX BY BINARY_INTEGER;
...
END colltype;
```
