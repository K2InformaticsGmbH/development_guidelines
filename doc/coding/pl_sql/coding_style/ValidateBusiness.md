[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Validate complex business rules with DML triggers](../../../../doc/coding/pl_sql/coding_style.md#ValidateBusiness)

Foreign key, `NOT NULL`, and check constraints provide mechanisms to validate simple business rules. However, there are cases they simply can't handle. In these cases, database triggers step in with the ability to support arbitrarily complex logic, while simultaneously guaranteeing that applications can't sidestep the rules.
