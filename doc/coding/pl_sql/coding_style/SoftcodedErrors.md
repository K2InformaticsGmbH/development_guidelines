[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Use named constants to soft-code application-specific error numbers and messages](../../../../doc/coding/pl_sql/coding_style.md#SoftcodedErrors)

Oracle allocates 1000 error numbers, between -20,000 and -20,999, to use for our own application-specific errors (such as "Employee must be 18 years old" or "Reservation date must be in the future").

Define all error numbers and their associated messages in a database table or operating-system file. Build a package that gives names to these errors, and then raise the errors using those names and not any hard-coded values.
