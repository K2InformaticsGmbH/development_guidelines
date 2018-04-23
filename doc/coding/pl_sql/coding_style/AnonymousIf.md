[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use anonymous blocks within `IF` statements to conserve resources](../../../../doc/coding/pl_sql/coding_style.md#AnonymousIf)

If you notice that certain operations and data structures aren't needed unless a certain condition is satisfied, move all the execution of those operations and the declaration of those data structures inside the conditional statement. The result is that you won't incur the overhead (CPU or memory) unless it's absolutely needed.

#### Instead of:

```PLSQL
DECLARE
    TYPE account_tabtype IS TABLE
        OF account%ROWTYPE INDEX BY BINARY_INTEGER;
    l_accounts account_tabtype;
    l_name VARCHAR2(2000) := min_balance_account (SYSDATE);
BEGIN
    IF balance_too_low (1056)
    THEN
        use_collection (l_accounts);
        use_name (l_name);
    ELSE
    -- No use of l_accounts or l_name
    ...
    END IF;
END;
```

#### it should be:

```PLSQL
BEGIN
    IF balance_too_low (1056)
    THEN
        DECLARE
            TYPE account_tabtype IS TABLE
                OF account%ROWTYPE INDEX BY BINARY_INTEGER;
            l_accounts account_tabtype;
            l_name VARCHAR2(2000) := min_balance_account (SYSDATE);
        BEGIN
            use_collection (l_accounts);
            use_name (l_name);
        END;
    ELSE
        -- No use of l_accounts or l_name
        ...
    END IF;
END;
```
