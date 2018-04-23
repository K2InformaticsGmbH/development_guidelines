[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Beware of and avoid implicit datatype conversions](../../../../doc/coding/pl_sql/coding_style.md#NoImplicit)

You should, however, avoid implicit conversions in your code. There are at least two big problems with relying on PL/SQL to convert data on your behalf:

- Conversion behavior can be non-intuitive. PL/SQL may convert data in ways that you don't expect, resulting in problems, especially within SQL statements.
- Conversion rules aren't under the control of the developer. These rules can change with an upgrade to a new version of Oracle or by changing RDBMSwide parameters, such as `NLS_DATE_FORMAT`.

You can convert explicitly using any of the following built-in functions: `TO_DATE`, `TO_CHAR`, `TO_NUMBER`, and `CAST`.
