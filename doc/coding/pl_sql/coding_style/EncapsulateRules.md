[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Encapsulate and name business rules and formulas behind function headers](../../../../doc/coding/pl_sql/coding_style.md#EncapsulateRules)

This is one of the most important best practices. The one aspect of any software project that never changes is that stuff always
changes. Business requirements, data structures, user interfaces: all these things change and change frequently. Your job as a programmer is to write code that adapts easily to these changes.

So whenever you need to express a business rule, put it inside a subroutine that hides the individual steps (which might change) and returns the results (if any).

And whenever you need a formula, express that formula inside its own function.
