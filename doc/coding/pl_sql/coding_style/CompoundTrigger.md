[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use compound triggers to consolidate all related trigger logic on a table](../../../../doc/coding/pl_sql/coding_style.md#CompoundTrigger)

The compound trigger has four timing-point sections:

- `BEFORE STATEMENT`: Consolidates all code that you need to run before the statement is executed. This would be the perfect place to reset any caching structures, for example.
- `BEFORE ROW`: Consolidates all code that you need to run before each row identified by the statement is executed.
- `AFTER ROW`: Consolidates all code that you need to run after each row identified by the statement is executed. If you are avoiding a mutating table error, you might take data from the row and place it in one or more collection caches.
- `AFTER STATEMENT`: Consolidates all code that you need to run after the statement is executed. This section, for example, is where you would place code to process DML operations that could not occur at the row level because of mutating table errors.

#### Skeleton trigger:

```PLSQL
CREATE TRIGGER <trigger_name>
BEFORE UPDATE ON <table>
COMPOUND TRIGGER
    /*
    Declare any variables here; they can be accessed anywhere
    inside the trigger body.
    */
    BEFORE STATEMENT IS
    BEGIN
        ...
    END BEFORE STATEMENT;
    BEFORE ROW IS
    BEGIN
        ...
    END BEFORE ROW;
    AFTER ROW IS
    BEGIN
        ...
    END AFTER ROW;
    AFTER STATEMENT IS
    BEGIN
        ...
    END AFTER STATEMENT;
END <trigger_name>;
```
