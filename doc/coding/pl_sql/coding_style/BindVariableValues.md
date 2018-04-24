[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Bind, do not concatenate, variable values into dynamic SQL strings](../../../../doc/coding/pl_sql/coding_style.md#BindVariableValues)

When you bind a variable value into a dynamic SQL string, you insert a "placeholder" into the string. This allows Oracle to parse a "generic" version of that SQL statement, which can be used over and over again, regardless of the actual value of the variable, without repeated parsing.

On the other hand, if you concatenate, then every time the value you concatenate changes, the physical SQL statement changes, causing excessive parsing.

#### Example:

Here's an example of binding with `DBMS_SQL`. This program updates any numeric column in the specified table, based on the supplied name:

```PLSQL
CREATE OR REPLACE PROCEDURE updnumval (
    tab_in IN VARCHAR2,
    namecol_in IN VARCHAR2,
    numcol_in IN VARCHAR2,
    name_in IN VARCHAR2,
    val_in IN NUMBER)
IS
    cur PLS_INTEGER;
    fdbk PLS_INTEGER;
BEGIN
    cur := open_and_parse (
        'UPDATE ' || tab_in ||
        ' SET ' || numcol_in || ' = :val
        WHERE ' || namecol_in || ' LIKE :name');

    DBMS_SQL.BIND_VARIABLE (cur, 'val', val_in);
    DBMS_SQL.BIND_VARIABLE (cur, 'name', name_in);

    fdbk := DBMS_SQL.EXECUTE (cur);

    DBMS_SQL.CLOSE_CURSOR (cur);
END;
/
```

Here's one possible usage of this procedure:

```PLSQL
SQL> exec updnumval ('emp', 'ename', 'sal', 'S%', 5000)
```
