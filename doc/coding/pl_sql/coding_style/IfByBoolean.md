[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Replace and simplify `IF` statements with Boolean expressions](../../../../doc/coding/pl_sql/coding_style.md#IfByBoolean)

Sometimes, you will write or come across conditional statements that, while valid, are unnecessary and cumbersome. Such statements often reflect a lack of understanding about how you can and should use Boolean expressions and variables.

#### Instead of:

```PLSQL
DECLARE
    boolean_variable BOOLEAN;
BEGIN
    IF boolean_variable = TRUE
    THEN
        ...
    ELSIF boolean_variable = FALSE
        65
    THEN
        ...
    END IF;
```

#### it should be:

```PLSQL
DECLARE
    boolean_variable BOOLEAN;
BEGIN
    IF boolean_variable
    THEN
        ...
    ELSIF NOT boolean_variable
    THEN
        ...
    END IF;
```
