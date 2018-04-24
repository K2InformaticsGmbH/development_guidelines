[Development Guidelines](../../../../README.md) / [Coding](../../../../README.md#coding) / [PL/SQL](../../../../README.md#coding_pl_sql) / [Coding Style](../../../../doc/coding/pl_sql/coding_style.md)

## [Freeze and build package specifications before implementing package bodies](../../../../doc/coding/pl_sql/coding_style.md#PackageSpec)

Develop a "specifications first" discipline: put off writing package bodies as long as possible. Instead, sit back, relax, and brainstorm about the kinds of things you want to do with each package. Write out those things-to-do as procedure and function headers in the specification. Do this for a whole bunch of packages you need to build.

Then try them out. Even if you don't built the package bodies, you can still write programs based on the headers. By doing this, you often uncover errors in the requirements, missing parameters, and so on. Since you haven't yet written the implementations, it's easy to clarify what the user wants and modify the package specifications.

Once you are confident that the specifications reflect the application needs, dive into those package bodies!
