[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use your own raise procedure in place of explicit calls to `RAISE_APPLICATION_ERROR`](../../../../doc/coding/pl_sql/coding_style.md#ApplicationError)

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
