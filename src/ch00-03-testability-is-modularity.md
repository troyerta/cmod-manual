# Testability is Modularity

If you're reading this guide, then you've probably had the chance to hear the arguments for Test-Driven Development.

If you've read the authoritative material on the matter, then you've also likely come across the stinging remark by James Grenning:

(Modular code is testable code)

Just like variables and functions should have a minimal scope, code modules should have a limited and focused span of concern within your codebase.

This drives clean interfaces between modules, and a strangely motivating need to achieve *consistency* between modules. Consistency in code style, interfacing, API, structure - everything. Your codebase then becomes easier and faster to navigate through, even for newbies to your project.

If testable code tends to be modular, can we likewise drive testability by formalizing the way we create code modules?

You bet we can.

Let's talk a deeper dive into project organization - deeper than you've ever wanted to.


