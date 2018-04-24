[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use the `EXCEPTION_INIT` pragma to name system exceptions that might be raised by your program](../../../../doc/coding/pl_sql/coding_style.md#ExceptionPragma)

There are hundreds upon hundreds of Oracle error codes and messages. Only a small handful are actually assigned a name for use in the PL/SQL language. This assignment occurs in the STANDARD package; here, for example, is the code defining the first three named exceptions in that package:

```PLSQL
CURSOR_ALREADY_OPEN exception;
    pragma EXCEPTION_INIT(CURSOR_ALREADY_OPEN, '-6511');
DUP_VAL_ON_INDEX exception;
    pragma EXCEPTION_INIT(DUP_VAL_ON_INDEX, '-0001');
TIMEOUT_ON_RESOURCE exception;
    pragma EXCEPTION_INIT(TIMEOUT_ON_RESOURCE, '-0051');
```

And since `STANDARD` is the default package, you can then write code in your own programs like:

```PLSQL
EXCEPTION
    WHEN CURSOR_ALREADY_OPEN THEN ...
```

You can also give names to system exceptions, and you should do so when your program might raise one of those exceptions.
