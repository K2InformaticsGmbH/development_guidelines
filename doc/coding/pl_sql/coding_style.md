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

- Set guidelines for application-wide error handling before you start coding. [(Details)](coding_style/ExceptionGuide.md) <a name="ExceptionGuide"></a>

#### Exceptions: Handling

#### Exceptions: Declarinng

#### Writing SQL in PL/SQL: General SQL and Transaction Management

#### Writing SQL in PL/SQL: Querying Data from PL/SQL

#### Writing SQL in PL/SQL: Changing Data from PL/SQL

#### Writing SQL in PL/SQL: Dynamic SQL and Dynamic PL/SQL

#### Program Construction: Structure and Parameters

- Avoid side-effects in your programs. [(Details)](coding_style/SideEffects.md) <a name="SideEffects"></a>
- Encapsulate and name business rules and formulas behind function headers. [(Details)](coding_style/EncapsulateRules.md) <a name="EncapsulateRules"></a>
- Limit execution section sizes to a single page using modularization. [(Details)](coding_style/LimitSize.md) <a name="LimitSize"></a>
- Standardize module structure using function and procedure templates. [(Details)](coding_style/StandardModule.md) <a name="StandardModule"></a>
- Use `NOCOPY` to minimize overhead when collections and records are [`IN`] `OUT` parameters. [(Details)](NocopyParameter/NocopyParameter.md) <a name="NocopyParameter"></a>
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

#### Built-in Packages: `UTL_FILE`

#### Built-in Packages: `DBMS_PIPE`

#### Built-in Packages: `DBMS_JOB`


