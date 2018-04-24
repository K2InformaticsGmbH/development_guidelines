[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Soft-code the maximum length of columns in `DBMS_SQL.DEFINE_COLUMN` calls](../../../../doc/coding/pl_sql/coding_style.md#SoftMaxLengths)

When you call `DBMS_SQL.DEFINE_COLUMN` to define a `VARCHAR2` column, you must provide the maximum length of the string that will be passed back to your program. Ideally, we'd use an attribute like `%COLLEN` to automatically draw that value from the data dictionary. There is, unfortunately, no such attribute. As a consequence, we usually sigh and hard-code a maximum length.

Rather than do that, create a package specification and place all column lengths you need to reference there. This way, if those lengths change, you can update just the one package. You can also generate this package specification directly from the data dictionary.

#### Example:

I create a "column length" package:

```PLSQL
CREATE OR REPLACE PACKAGE collen
IS
    city CONSTANT INTEGER := 15;
    state CONSTANT INTEGER := 2;
END collen;
```

And I now reference those constants whenever I call `DBMS_SQL.DEFINE COLUMN`:

```PLSQL
DBMS_SQL.DEFINE_COLUMN (
    cursor_handle, 1, city, collen.city);

DBMS_SQL.DEFINE_COLUMN (
    cursor_handle, 2, state, collen.state);
```
