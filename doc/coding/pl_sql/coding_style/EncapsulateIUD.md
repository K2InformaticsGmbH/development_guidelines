[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Encapsulate INSERT, UPDATE, and DELETE statements behind procedure calls](../../../../doc/coding/pl_sql/coding_style.md#EncapsulateIUD)

Write a standalone procedure or put such procedures inside a single "table
encapsulation package," but never, ever embed DML statements directly within
application code.

#### Example:

Instead of writing an `INSERT` as follows:

```PLSQL
INSERT INTO book (
    isbn, title, author)
VALUES (
    '1-56592-675-7',
    'Oracle PL/SQL Programming Guide to Oracle8i Features',
    'Feuerstein, Steven');
```

use a standalone procedure, as in:

```PLSQL
add_book (
    '1-56592-675-7',
    'Oracle PL/SQL Programming Guide to Oracle8i Features',
    'Feuerstein, Steven');
```

or a packaged procedure:

```PLSQL
te_book.ins (
'1-56592-675-7',
'Oracle PL/SQL Programming Guide to Oracle8i Features',
'Feuerstein, Steven');
```
