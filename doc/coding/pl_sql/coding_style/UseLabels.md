[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use block and loop labels](../../../../doc/coding/pl_sql/coding_style.md#UseLabels)

Use a label directly in front of loops and nested anonymous blocks:
- To name that portion of code and thereby self-document what it's doing
- So you can repeat that name with the `END` statement of that block or loop

This is especially important when you have multiple nestings of loops as in the following:

```pl/sql
LOOP
    <body>
    WHILE <condition>
    LOOP
        while body>
    END LOOP;    
END LOOP;
```
