[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Do not hard-code `VARCHAR2` lengths](../../../../doc/coding/pl_sql/coding_style.md#HardcodeVarchar2)

In general, you shouldn't hard-code your datatypes; instead, you should rely
on anchoring and `SUBTYPEs`.
