[Development Guidelines](../../../README.md) / [Version Control](../../../README.md#version_control) / [GitHub](../../../README.md#github)

## [Badges](../../../README.md#version_control_github)

### 1 File Names

File Type | Extension
:--------- | :---------:
Package body | pkb
Package (or package specification) | pks
Function | fnc
Procedure | prc
Trigger | trg
Object type body | tpb
Object type (or object type specification) | tps
Any other PL/SQL | pls
Any other SQL | sql

----

### 2 Identifier Names

#### 2.1 Must

- The total **length** of an identifier name is limited to 30 characters.
- Make **plural** anything that contains multiple pieces of information. 
- Name **procedures** with verb phrases and **functions** with noun phrases.
- If you have more than one **record** declared for a single cursor, preface the record name with a word that describes it,
- The **root name** of the identifier is the part of the identifier name that describes concisely and accurately the meaning of the thing named.
- The **scope prefix** (SC) is either `g_` for global, `l_` for local or `p_` for parameters.
- **Upper-case** non-application identifiers (elements of the PL/SQL and SQL language and Oracle built-ins) and **lower-case** application specific elements.

----

#### 2.2 Avoid

- Using names like `i` and `j`.
- Including an indicator of the **datatype** in the name, as in `g_i_counter`.
- Using names defined in the `STANDARD` and `DBMS_STANDARD` **packages**.
- **Recycling** names.
- **Repeating** names at different scopes.
- **Starting** your procedures with `p_` / `sp_` or functions with `f_` / `sf_`.
 
---- 

Naming convention | Type of identifier | Example 
:---------------- | :----------------- | -------          
`c_rootname`       | constant declared in a PL/SQL block | `c_max_salary` 
`e_rootname`       | exception | `e_balance_too_low` 
`en_rootname`      | exception number (a constant that is assigned the value of an error code)                              | `en_balance_too_low CONSTANT PLS_INTEGER = -20555` 
`g_rootname`       | variable declared at the package level | `g_total_sales` 
`gc_rootname`      | constant declared at the package level | `gc_max_salary` 
`l_rootname`       | variable declared in a PL/SQL block | `l_total_sales` 
`p_rootname_in`    | `IN` parameter | `p_salary_in` 
`p_rootname_inout` | `IN OUT` parameter | `p_salary_inout` 
`p_rootname_out`   | `OUT` parameter | `p_salary_out` 
`SC_rootname_aat`  | associative array collection (plural) | `l_employees_aat` 
`SC_rootname_aatv` | associative array collection variable (plural) | `l_employees_aatv` 
`SC_rootname_cur`  | cursor declaration (plural) | `l_employees_cur` 
`SC_rootname_cv`   | cursor variable | `l_name_and_salary_cv` 
`SC_rootname_nt`   | nested table collection (plural) | `l_employees_nt` 
`SC_rootname_ntv`  | nested table collection variable (plural) | `l_employees_ntv` 
`SC_rootname_ot`   | object type | `l_employee_ot` 
`SC_rootname_rt`   | record type (singular) | `l_name_and_salary_rt` 
`SC_rootname_rtv`  | record variable | `l_employee_rtv` 
`SC_rootname_vat`  | `VARRAY` collection (plural) | `l_employees_vat`
`SC_rootname_vatv` | `VARRAY` collection variable (plural) | `l_employees_vatv`

----

#### 2.3 Standard prefixes for procedure verb names

Prefix | Procedure activity 
:----- | :------------------
`chk_` | validates something
`cre_` | creates something
`del_` | deletes something
`get_` | selects something
`ins_` | inserts something
`upd_` | updates something
