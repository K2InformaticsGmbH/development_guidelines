[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Consolidate “overlapping” DML triggers to control execution order, or use the `FOLLOWS` syntax](../../../../doc/coding/pl_sql/coding_style.md#TriggerFollow)

Oracle has a `FOLLOWS` clause so that you can dictate the order of execution:

```PLSQL
CREATE OR REPLACE TRIGGER <trigger_new>
FOLLOWS <trigger_original>
    ...
END;
```

and then Oracle will always execute the new trigger after the original trigger.
