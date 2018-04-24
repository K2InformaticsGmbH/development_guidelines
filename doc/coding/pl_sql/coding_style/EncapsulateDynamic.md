[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Encapsulate dynamic SQL parsing to improve error detection and cleanup](../../../../doc/coding/pl_sql/coding_style.md#EncapsulateDynamic)

"Dynamic" means that the SQL statement or PL/SQL block that you execute is constructed, parsed, and compiled at runtime, not at the time the code is compiled. Dynamic SQL offers a tremendous amount of flexibility - but also complexity.

Dynamic SQL is tricky; you generally glue together different chunks of text (with the concatenation operator) to form what you hope is a valid SQL or PL/SQL statement.

Either through programmer error or user error, you can end up with a bad chunk of SQL, resulting in a parse error.

To identify and fix these errors, you should create your own parsing "engine" on top of `DBMS_SQL.PARSE` and the NDS statements. This program traps and displays error information, and cleans up any cursors.

#### Example:

This technique is most crucial for DBMS_SQL. Don't ever call `DBMS_SQL.PARSE` directly in your program. Instead, call your own parse encapsulator. Why would you bother to do this? Consider the following block of code. It leaves a DBMS_SQL cursor unclosed and unclosable; you need to be able to reference the dyncur variable in the call to `DBMS_SQL.CLOSE_CURSOR`, but that variable is erased once the exception is
propagated:

```PLSQL
DECLARE
    dyncur PLS_INTEGER := DBMS_SQL.open_cursor;
BEGIN
    -- Whoops, forget the FROM clause!
    DBMS_SQL.parse (
        dyncur, 'select * dual', DBMS_SQL.native);
END;
```

Here's a very simple example of an encapsulation for `DBMS_SQL.PARSE`:

```PLSQL
CREATE OR REPLACE FUNCTION open_and_parse (
    dynsql_in IN VARCHAR2,
    dbms_mode_in IN INTEGER := NULL)
RETURN INTEGER
IS
    dyncur INTEGER;
BEGIN
    dyncur := DBMS_SQL.OPEN_CURSOR;
    DBMS_SQL.PARSE (dyncur, dynsql_in,
    NVL (dbms_mode_in, DBMS_SQL.NATIVE));
    RETURN dyncur;
EXCEPTION
    WHEN OTHERS
    THEN
        DBMS_SQL.CLOSE_CURSOR (dyncur);
        pl (SQLERRM);
        pl (dynsql_in);
        RETURN NULL;
END;
/
```

Here's the native dynamic SQL equivalent:

```PLSQL
CREATE OR REPLACE PROCEDURE exec_immed (
    dynsql_in IN VARCHAR2)
    AUTHID CURRENT_USER
IS
BEGIN
    EXECUTE IMMEDIATE dynsql_in;
EXCEPTION
    WHEN OTHERS
    THEN
        pl (SQLERRM)
        pl (dynsql_in);
END;
/
```

