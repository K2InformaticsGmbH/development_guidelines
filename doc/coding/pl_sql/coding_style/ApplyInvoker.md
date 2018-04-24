[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Apply the invoker rights method to all stored code that executes dynamic SQL](../../../../doc/coding/pl_sql/coding_style.md#ApplyInvoker)

Whenever you create a stored program (standalone or within a package) that parses a dynamic SQL statement, you should define that program with the "invoker rights" model. This is done by adding the following clause to the program header:

```PLSQL
AUTHID CURRENT_USER
```

This clause ensures that the dynamic SQL string is parsed under the authority of the schema currently running the program, which is almost always the desired behavior.

#### Example:

If I were to create a reusable program to execute any DDL statement, I would make certain it used the `AUTHID` statement as follows:

```PLSQL
CREATE OR REPLACE PROCEDURE runddl (
    ddl_in in VARCHAR2)
    AUTHID CURRENT_USER
IS
BEGIN
    EXECUTE IMMEDIATE ddl_in;
EXCEPTION
    WHEN OTHERS
    THEN
        pl (SQLERRM)
        pl (ddl_in);
        RAISE;
END;
```




















When it comes to managing errors, Oracle requires a lot of developers. If you're raising a "system" exception like NO_DATA_FOUND, you use RAISE. But when you want to raise an application-specific error, you use RAISE_APPLICATION_ERROR. If you use the latter, you have to provide an error number and message. This leads to unnecessary and damaging hard coding.

A more fail-safe approach is to provide a predefined raise procedure that automatically checks the error number and determines the correct way to raise the error.

#### Example:

Instead of writing code like this:

```PLSQL
RAISE_APPLICATION_ERROR (
-20734,
'Employee must be 18 years old.');
```

you should write code like this:

```PLSQL
err.raise (errnums.emp_too_young);
```

#### Challenges

First, you must set your standards on what kind of exceptions (the numbers and messages, in particular) you will use for your application. Then you need to make sure that everyone uses the `err.raise` procedure.
