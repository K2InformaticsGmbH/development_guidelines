[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use a single `EXIT` in simple loops](../../../../doc/coding/pl_sql/coding_style.md#SimpleExit)

This best practice is another variation on "one way in, one way out." It suggests that, whenever possible, you consolidate all exit logic in your simple loop to a single `EXIT` (or `EXIT WHEN`) statement.

In general, use the `EXIT WHEN` statement in place of code like this:

```PLSQL
IF <> THEN EXIT; END IF;
```

because it's more intuitive and requires less typing.

#### Instead of:

```PLSQL
LOOP
    read_line (file1, line1, file1_eof);
    read_line (file2, line2, file2_eof);
    
    IF (file1_eof AND file2_eof)
    THEN
        retval := TRUE;
        EXIT;
    ELSIF (line1 != line2)
    THEN
        retval := FALSE;
        EXIT;
    ELSIF (file1_eof OR file2_eof)
    THEN
        retval := FALSE;
        EXIT;
    END IF;
END LOOP;
```

#### it should be:

```PLSQL
LOOP
    read_line (file1, line1, file1_eof);
    read_line (file2, line2, file2_eof);
    
    IF (file1_eof AND file2_eof)
    THEN
        retval := TRUE;
        exit_loop := TRUE;
    ELSIF (line1 != line2)
    THEN
        retval := FALSE;
        exit_loop := TRUE;
    ELSIF (file1_eof OR file2_eof)
    THEN
        retval := FALSE;
        exit_loop := TRUE;
    END IF;
    EXIT WHEN exit_loop;
END LOOP;
```
