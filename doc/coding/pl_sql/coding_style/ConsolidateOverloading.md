[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Consolidate the implementation of related overloaded modules](../../../../doc/coding/pl_sql/coding_style.md#ConsolidateOverloading)

In most cases, when you build overloaded programs, each program performs a similar operation, with variations that are usually related to different combinations of parameters. If you aren't careful about how you implement these overloadings, you will end up with a mess of code that's difficult to maintain and enhance.

The most important step you can take is to isolate behavior/features common to all overloadings and then move that common code into a separate, usually private program. All the overloadings then call that internal program.

You should also take care to organize the overloaded headers contiguously in the package specification so that they are easily identified.
