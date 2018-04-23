[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use `SUBTYPE` to standardize application-specific datatypes](../../../../doc/coding/pl_sql/coding_style.md#UseSubtype)

The `SUBTYPE` statement allows you to create "aliases" for existing types of information, in effect creating your own specially named datatypes. Use `SUBTYPE` when you want to standardize on a set of named datatypes that aren't anchorable back to the database.

#### Example:

Define the `SUBTYPE`

```pl/sql
CREATE OR REPLACE PACKAGE book_data
IS
    SUBTYPE total_count_t IS INTEGER (10);
```

and then use that in the declaration section:

```pl/sql
DECLARE
l_total book_data.total_count_t;
```
