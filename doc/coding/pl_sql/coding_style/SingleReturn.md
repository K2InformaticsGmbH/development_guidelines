[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Limit functions to a single `RETURN` statement in the execution section](../../../../doc/coding/pl_sql/coding_style.md#SingleReturn)

A good general rule to follow as you write your PL/SQL programs is: "one way in and one way out." In other words, there should be just one way to enter or call a program (there is; you don't have any choice in this matter). And there should be one way out, one exit path from a program (or loop) on successful termination. By following this rule, you end up with code that is much easier to trace, debug, and
maintain.

For a function, this means you should think of the executable section as a funnel; all the lines of code narrow down to the last executable statement:

```PLSQL
RETURN return value;
```

Note the following:
- You can, and should, still have `RETURN` statements in your exception handlers. Not every exception should be passed unhandled from your function.
- It's possible (i.e., acceptable syntax) to use an "unqualified" `RETURN` statement in a procedure and the procedure immediately terminates and returns control. You shouldn't do this, however, as it results in unstructured code that's hard to debug and maintain This same recommendation holds for the initialization section of a package.

```PLSQL
IF all_done
THEN
    RETURN;
END IF;
```
