[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Never declare the `FOR` loop index](../../../../doc/coding/pl_sql/coding_style.md#NeverForLoop)

PL/SQL offers two kinds of `FOR` loops: numeric and cursor. Both have this general format:

```PLSQL
FOR loop index IN loop range
LOOP
    loop body
END LOOP;
```

The loop index is either an integer or a record; in either case, it's implicitly declared by the PL/SQL runtime engine. The scope of the loop index variable is restricted to the body of the loop (between the `LOOP` and `END LOOP` statements).

You should never declare a variable for the loop. If you do declare the loop index variable, you are actually declaring a completely separate (recordtype or numeric) variable that will (best case) never be used or (worst case) used outside the loop in a way that is confusing and likely to introduce errors.
