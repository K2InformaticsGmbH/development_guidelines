[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Provide well-defined interfaces to business data and functional manipulation using packages](../../../../doc/coding/pl_sql/coding_style.md#InterfacePackage)

Humans can handle only so much complexity at once. The details and nuances of any decent-sized application overwhelm the human mind. Use packages to hide - or at least attempt to organize - the mind-boggling complexity. Expose the underlying data and business rules in an orderly and manageable fashion through the package specification.

This technique is crucially important when implementing core business rules in your application. Every such rule should be hidden behind a function and defined in the appropriate package.

In addition, hide all the SQL for a given table or business entity behind a package interface (this process is called table encapsulation). Rather than write an `INSERT` statement in your program, call an insert procedure.
