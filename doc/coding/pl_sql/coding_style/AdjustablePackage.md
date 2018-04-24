[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Implement flexible, user-adjustable functionality using package state toggles and related techniques](../../../../doc/coding/pl_sql/coding_style.md#AdjustablePackage)

As you rely more and more on packages to offer functionality to programmers on your team or in your company, you want to design those packages to be flexible and responsive to varying user needs.

You certainly don't want programmers going into the package bodies and changing implementations. You also don't want them making copies of your code and then producing their own variations.

Instead, add programs to the package specification that allow developers to modify (within certain accepted pathways) the behavior of your package to fit their varying requirements. These programs might turn on/off certain features ("toggles") or might set internal package values.

The most important feature of these programs is that they allow the package to change its behavior without having to change the source code
