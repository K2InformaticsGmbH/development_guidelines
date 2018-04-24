[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Build trace "windows" into your packages using standardized programs](../../../../doc/coding/pl_sql/coding_style.md#PackageTrace)

On the one hand, it's very helpful to use packages to hide complexity. On the other hand, it's often the case that users can be greatly aided by being able to look inside packages and watch what's happening.

You can easily build a "read-only" window into a package. Users can open the window when and if he wants to, watch what the package is doing (or at least what the author of the package claims the package is doing), and then shut the window when that information isn't needed.

To build a window, you will need to:

- Add tracing code inside the package body.
- Supply an on-off switch in the specification so that users can open and close the window.
