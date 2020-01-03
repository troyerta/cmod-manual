## Assumptions & Requirements

Cmod is based on use of a few widely available, and popular tools already found in many C project development environments:

Requirements for the development environment:
(These tools must be accessible from the command line / system PATH)
- Python 3.7.0 (no Python 2 support)
- GNU Make
- GCC C compiler

Recommended Experience for Developer (but not required):
- Python basics
- How C programs are built
- Make / Makefiles
- Test-Driven Development Techniques, XUnit-style tests

### Why does Cmod use these tools and not others?

Cmod makes use of these tools for a number of reasons:

- These tools are each available for all major OS platforms (Windows, Linux, Mac)

- They are not new, and not obscure. They each have long proven histories of use in industry, and don't rely on any proprietary vendors. Being open-source, these tools will be around forever.

- Maintainability is high for these tools, meaning if anything about your use of these tools needs to change, it will be fairly simple. These tools are relatively simple to understand, and you can find *many* online examples of how to adjust these tools.

All in all, these requirements are simple ones. Cmod does not ask much of your development PC. Having Make, a C compiler, and an up-to-date to Python 3.8 installation (Python 2 is deprecated) is all basic stuff to have.

That said, here are the Debian/Ubuntu commands for checking for correction installation:

```shell
$ python3.8 --version
Python 3.8.0
```

```shell
$ make --version
GNU Make 4.1
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```
All good to go? If not you need to get these tools installed and added to your system PATH.
