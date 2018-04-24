[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Avoid bloating package code with unnecessary but easy-to-build modules](../../../../doc/coding/pl_sql/coding_style.md#AvoidBloating)

Once you get started building packages, especially packages that provide an interface to underlying functionality, it's so, so easy to get excited about all the possibilities, all the different programs that can and should be a part of that interface.

The result can be best characterized by a rephrasing of that oft-repeated riddle:

If you write a program and no one uses it, does that program really exist?

And it's not just a matter of wasted effort. By loading up a package with programs no one necessarily wants or needs, you make it harder for anyone to find the programs that they actually do want or need. You are better off taking a minimalist approach to building your packages: build only what is needed at this point in time. Implement those requirements in the simplest, most direct manner possible.
