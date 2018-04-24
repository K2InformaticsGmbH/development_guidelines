[Development Guidelines](../../../README.md) / [Coding](../../../README.md#coding) / [PL/SQL](../../../README.md#coding_pl_sql)

## [Coding Style](../../../README.md#coding_pl_sql_coding_style)

#### Coding Style and Conventions

- Standardize module and program headers. [(Details)](coding_style/StdHeader.md) <a name="StdHeader"></a>
- Tag module `END` statements with module names. [(Details)](coding_style/TagEND.md) <a name="TagEnd"></a>
- Use block and loop labels. [(Details)](coding_style/UseLabels.md) <a name="UseLabels"></a>

#### Variables and Data Structures: Declaring

- Anchor variables to database datatypes using `%TYPE` and `%ROWTYPE`. [(Details)](coding_style/AnchorTypes.md) <a name="AnchorTypes"></a>
- Do not hard-code `VARCHAR2` lengths. [(Details)](coding_style/HardcodeVarchar2.md) <a name="HardcodeVarchar2"></a>
- Match datatypes to computational usage. [(Details)](coding_style/MatchDataTypes.md) <a name="MatchDataTypes"></a>
- Perform complex variable initialization in the executable section. [(Details)](coding_style/ComplexExec.md) <a name="ComplexExec"></a>
- Use `CONSTANT` declarations for variables whose values do not change. [(Details)](coding_style/UseConstant.md) <a name="UseConstant"></a>
- Use `SUBTYPE` to standardize application-specific datatypes. [(Details)](coding_style/UseSubtype.md) <a name="UseSubtype"></a>

#### Variables and Data Structures: Using

- Beware of and avoid implicit datatype conversions. [(Details)](coding_style/NoImplicit.md) <a name="NoImplicit"></a>
- Clean up data structures when your program terminates (successfully or with an error). [(Details)](coding_style/CleanUpDS.md) <a name="CleanUpDS"></a>
- Do not overload data structure usage. [(Details)](coding_style/OverloadDS.md) <a name="OverloadDS"></a>
- Remove unused variables and code. [(Details)](coding_style/RemoveUnused.md) <a name="RemoveUnused"></a>
- Replace complex expressions with Boolean variables and functions. [(Details)](coding_style/ComplexBoolean.md) <a name="ComplexBoolean"></a>

#### Variables and Data Structures:     Package Variables

- Centralize `TYPE` definitions in package specifications. [(Details)](coding_style/CentralizeTypes.md) <a name="CentralizeTypes"></a>
- Expose package globals using "get and set" modules. [(Details)](coding_style/ExposeGetSet.md) <a name="ExposeGetSet"></a>
- Package application-named literal constants together. [(Details)](coding_style/PackAppConst.md) <a name="PackAppConst"></a>
- Use package globals judiciously and only in package bodies. [(Details)](coding_style/PackageGlobals.md) <a name="PackageGlobals"></a>

#### Control Structures: Conditional and Boolean Logic

- Replace and simplify `IF` statements with Boolean expressions. [(Details)](coding_style/IfByBoolean.md) <a name="IfByBoolean"></a>
- Use `ELSIF` with mutually exclusive clauses. [(Details)](coding_style/ElseIfMutually.md) <a name="ElseIfMutually"></a>
- Use `IF`...`ELSIF` only to test a single, simple condition. [(Details)](coding_style/ElseIfSimple.md) <a name="ElseIfSimple"></a>

#### Control Structures: Loop Processing

- Move static expressions outside of loops and SQL statements. [(Details)](coding_style/StaticLoop.md) <a name="StaticLoop"></a>
- Never `EXIT` or `RETURN` from `WHILE` and `FOR` loops. [(Details)](coding_style/NeverExit.md) <a name="NeverExit"></a>
- Never declare the `FOR` loop index. [(Details)](coding_style/NeverForLoop.md) <a name="NeverForLoop"></a>
- Scan collections using `FIRST`, `LAST`, and `NEXT` in loops. [(Details)](coding_style/FirstLastNext.md) <a name="FirstLastNext"></a>
- Use a simple loop to avoid redundant code required by a `WHILE` loop. [(Details)](coding_style/SimpleLoop.md) <a name="SimpleLoop"></a>
- Use a single `EXIT` in simple loops. [(Details)](coding_style/SimpleExit.md) <a name="SimpleExit"></a>

#### Control Structures: Miscellaneous

- Use anonymous blocks within `IF` statements to conserve resources. [(Details)](coding_style/AnonymousIf.md) <a name="AnonymousIf"></a>

#### Exceptions: Raising

- Catch all exceptions and convert to meaningful return codes before returning to non-PL/SQL host programs. [(Details)](coding_style/CatchExceptions.md) <a name="CatchExceptions"></a>
- Do not overload an exception with multiple errors unless the loss of information is intentional. [(Details)](coding_style/OverloadExceptions.md) <a name="OverloadExceptions"></a>
- Only `RAISE` exceptions for errors, not to branch execution control. [(Details)](coding_style/OnlyErrors.md) <a name="OnlyErrors"></a>
- Set guidelines for application-wide error handling before you start coding. [(Details)](coding_style/ExceptionGuide.md) <a name="ExceptionGuide"></a>
- Use the default exception-handling model to communicate module status back to calling PL/SQL programs. [(Details)](coding_style/DefaultModel.md) <a name="DefaultModel"></a>
- Use your own raise procedure in place of explicit calls to `RAISE_APPLICATION_ERROR`. [(Details)](coding_style/ApplicationError.md) <a name="ApplicationError"></a>

#### Exceptions: Handling

- Avoid hard-coded exposure of error handling by using standard, declarative procedures. [(Details)](coding_style/AvoidExposure.md) <a name="AvoidExposure"></a>
- Handle exceptions that cannot be avoided but can be anticipated. [(Details)](coding_style/HandleAvoided.md) <a name="HandleAvoided"></a>
- Include standardized modules in packages to dump package state when errors occur. [(Details)](coding_style/DumpErrors.md) <a name="DumpErrors"></a>
- Use `WHEN OTHERS` only for unknown exceptions that need to be trapped. [(Details)](coding_style/WhenOthers.md) <a name="WhenOthers"></a>
- Use named constants to soft-code application-specific error numbers and messages. [(Details)](coding_style/SoftcodedErrors.md) <a name="SoftcodedErrors"></a>

#### Exceptions: Declaring

- Document all package exceptions by module in package specifications. [(Details)](coding_style/DocuExceptions.md) <a name="DocuExceptions"></a>
- Standardize named application exceptions in package specifications. [(Details)](coding_style/StdNamedException.md) <a name="StdNamedException"></a>
- Use the `EXCEPTION_INIT` pragma to name system exceptions that might be raised by your program. [(Details)](coding_style/ExceptionPragma.md) <a name="ExceptionPragma"></a>

#### Writing SQL in PL/SQL: General SQL and Transaction Management

- Qualify PL/SQL variables with their scope names when referenced inside SQL statements. [(Details)](coding_style/QualifyVariables.md) <a name="QualifyVariables"></a>
- Use autonomous transactions to isolate the effect of `COMMITs` and `ROLLBACKs`. [(Details)](coding_style/AutoTransaction.md) <a name="AutoTransaction"></a>
- Use incremental `COMMITs` to avoid rollback segment errors when changing large numbers of rows. [(Details)](coding_style/IncrementalCommit.md) <a name="IncrementalCommit"></a>

#### Writing SQL in PL/SQL: Querying Data from PL/SQL

- Define multi-row cursors in packages so they can be used from multiple programs. [(Details)](coding_style/MultiRowFetch.md) <a name="MultiRowFetch"></a>
- Fetch into cursor records, never into a hard-coded list of variables. [(Details)](coding_style/NeverFetchHard.md) <a name="NeverFetchHard"></a>
- Hide reliance on the dual table. [(Details)](coding_style/HideDual.md) <a name="HideDual"></a>
- Never use a cursor `FOR` loop to fetch just one row. [(Details)](coding_style/Fetch1Row.md) <a name="Fetch1Row"></a>
- Parameterize explicit cursors. [(Details)](coding_style/ParamExplCursors.md) <a name="ParamExplCursors"></a>
- Put single-row fetches inside functions; never hard-code a query in your block. [(Details)](coding_style/SingleRowFetch.md) <a name="SingleRowFetch"></a>
- Specify columns to be updated in a `SELECT FOR UPDATE` statement. [(Details)](coding_style/SelectForUpdate.md) <a name="SelectForUpdate"></a>
- Use `BULK COLLECT` to improve performance of multi-row queries. [(Details)](coding_style/UseBulkCollect.md) <a name="UseBulkCollect"></a>
- Use `COUNT` only when the actual number of occurrences is needed. [(Details)](coding_style/CountOnly.md) <a name="CountOnly"></a>
- Use `RETURNING` to retrieve information about modified rows. [(Details)](coding_style/ReturningMod.md) <a name="ReturningMod"></a>
- Use a cursor `FOR` loop to fetch all rows in a cursor unconditionally. [(Details)](coding_style/CursorForLoop.md) <a name="CursorForLoop"></a>

#### Writing SQL in PL/SQL: Changing Data from PL/SQL

- Check `SQL%ROWCOUNT` when updating or removing data that "should" be there. [(Details)](coding_style/CheckUpdating.md) <a name="CheckUpdating"></a>
- Encapsulate INSERT, UPDATE, and DELETE statements behind procedure calls. [(Details)](coding_style/EncapsulateIUD.md) <a name="EncapsulateIUD"></a>
- Reference cursor attributes immediately after executing the SQL operation. [(Details)](coding_style/RefCursorAttr.md) <a name="RefCursorAttr"></a>
- Use `FORALL` to improve performance of collection-based DML. [(Details)](coding_style/UseForAll.md) <a name="UseForAll"></a>

#### Writing SQL in PL/SQL: Dynamic SQL and Dynamic PL/SQL

- Apply the invoker rights method to all stored code that executes dynamic SQL. [(Details)](coding_style/ApplyInvoker.md) <a name="ApplyInvoker"></a>
- Bind, do not concatenate, variable values into dynamic SQL strings. [(Details)](coding_style/BindVariableValues.md) <a name="BindVariableValues"></a>
- Encapsulate dynamic SQL parsing to improve error detection and cleanup. [(Details)](coding_style/EncapsulateDynamic.md) <a name="EncapsulateDynamic"></a>
- Format dynamic SQL strings so they can be easily read and maintained. [(Details)](coding_style/FormatDynamic.md) <a name="FormatDynamic"></a>
- Soft-code the maximum length of columns in `DBMS_SQL.DEFINE_COLUMN` calls. [(Details)](coding_style/SoftMaxLengths.md) <a name="SoftMaxLengths"></a>

#### Program Construction: Structure and Parameters

- Avoid side-effects in your programs. [(Details)](coding_style/SideEffects.md) <a name="SideEffects"></a>
- Encapsulate and name business rules and formulas behind function headers. [(Details)](coding_style/EncapsulateRules.md) <a name="EncapsulateRules"></a>
- Limit execution section sizes to a single page using modularization. [(Details)](coding_style/LimitSize.md) <a name="LimitSize"></a>
- Standardize module structure using function and procedure templates. [(Details)](coding_style/StandardModule.md) <a name="StandardModule"></a>
- Use `NOCOPY` to minimize overhead when collections and records are [`IN`] `OUT` parameters. [(Details)](coding_style/NocopyParameter.md) <a name="NocopyParameter"></a>
- Use named notation to clarify, self-document, and simplify module calls. [(Details)](coding_style/NamedNotation.md) <a name="NamedNotation"></a>

#### Program Construction: Functions

- Limit functions to a single `RETURN` statement in the execution section. [(Details)](coding_style/SingleReturn.md) <a name="SingleReturn"></a>
- Keep functions pure by avoiding [`IN`] `OUT` parameters. [(Details)](coding_style/PureFunctions.md) <a name="PureFunctions"></a>
- Never return `NULL` from Boolean functions. [(Details)](coding_style/NeverNull.md) <a name="NeverNull"></a>

#### Program Construction: Triggers

- Consolidate “overlapping” DML triggers to control execution order, or use the `FOLLOW` syntax. [(Details)](coding_style/TriggerFollow.md) <a name="TriggerFollow"></a>
- Use compound triggers to consolidate all related trigger logic on a table. [(Details)](coding_style/CompoundTrigger.md) <a name="CompoundTrigger"></a>
- Validate complex business rules with DML triggers. [(Details)](coding_style/ValidateBusiness.md) <a name="ValidateBusiness"></a>

#### Package Construction

- Avoid bloating package code with unnecessary but easy-to-build modules. [(Details)](coding_style/AvoidBloating.md) <a name="AvoidBloating"></a>
- Build trace "windows" into your packages using standardized programs. [(Details)](coding_style/PackageTrace.md) <a name="PackageTrace"></a>
- Consolidate the implementation of related overloaded modules. [(Details)](coding_style/ConsolidateOverloading.md) <a name="ConsolidateOverloading"></a>
- Freeze and build package specifications before implementing package bodies. [(Details)](coding_style/PackageSpec.md) <a name="PackageSpec"></a>
- Group related data structures and functionality together in a single package. [(Details)](coding_style/GroupRelated.md) <a name="GroupRelated"></a>
- Implement flexible, user-adjustable functionality using package state toggles and related techniques. [(Details)](coding_style/AdjustablePackage.md) <a name="AdjustablePackage"></a>
- Insulate applications from Oracle version sensitivity using version-specific implementations. [(Details)](coding_style/VersionSpecific.md) <a name="VersionSpecific"></a>
- Provide well-defined interfaces to business data and functional manipulation using packages. [(Details)](coding_style/InterfacePackage.md) <a name="InterfacePackage"></a>
- Separate package specifications and bodies into different source code files. [(Details)](coding_style/SeparateSpecBody.md) <a name="SeparateSpecBody"></a>
- Simplify and encourage module usage using overloading to widen calling options. [(Details)](coding_style/UsingOverloading.md) <a name="UsingOverloading"></a>
- Use a standard format for packages that include comment headers for each type of element defined in the package. [(Details)](coding_style/PackageStandard.md) <a name="PackageStandard"></a>
- Use package body persistent data structures to cache and optimize data-driven processing. [(Details)](coding_style/BodyPersistent.md) <a name="BodyPersistent"></a>

#### Built-in Packages: `DBMS_OUTPUT`

- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>

#### Built-in Packages: `UTL_FILE`

- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>

#### Built-in Packages: `DBMS_PIPE`

- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>

#### Built-in Packages: `DBMS_JOB`

- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>
- xxx. [(Details)](coding_style/yyy.md) <a name="yyy"></a>

