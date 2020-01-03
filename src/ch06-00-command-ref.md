# Quick Reference

But why do we need to have a python virtual environment?

This is an important abstraction layer of sorts. Using a Python virtual environment (venv) ensures your project's use of python and and python libraries and modules does not force any PC developing on your project to have those modules and libraries installed system-wide. This allows all your team members to use their own host-OS, reducing the number of third party requirements for building your project.

Python allows this with it's venv module, which creates a local instance of a Python installation **in the project** for the development on this project on this machine. But this directory and all it's binary blobs are not added to source control so your peers or coworkers can clone the project, and setup a local Python installation instance (virtual environment) that works on their machine and host OS. It only takes a couple terminal commands to do this, so once your project is cloned, it's just a couple more

Python scripts are a little less portable than Perl or Ruby scripts can be. I attribute this to Python's relative instability as a language over the last 10 years. Python's popularity surge in this time came with a number of features and changes that broke older Python scripts, but there were also a number of great modules and utilities that make Python a joy to use. It has become much more stable as a language to use since then. So there is something to be said for having an updated installation of Python. 3.8 is recommended for CMod. But, if you need to use a legacy version instead, you can specify the version you need with the venv command.








Cmod is a collection of python scripts and classes that support structured software development technqiues,
which in turn, simplifies other tasks like unit testing, TDD, and general code maintainence. Once you try it out
with a simple demo project, you'll see why this may be especially helpful for embedded systems projects using the
C language.

Here's the main thing you need to know about Cmod before you integrate it into a project:
Cmod allows you to manage your project as a collection of testable modules.

Cmod's definition of a module is just a directory in your project that contains a special file marking it as so.
This lets you populate your modules with as much or as little production code as you like, since there is no
agreed-upon definition of the heavily abused term "module".

With Cmod's module definition, it is advisable to start organizing your code using a block diagram. It should show your project's
varying code units, and how they relate to each other in the project directory - not necessarily how they might depend on one-another.

Block diagrams add a large number of organizational benefits to your project - even before you have any code written, so
take some time to draw yourself a picture of what you want to codebase to look and feel like.

Use the back of a napkin to start, or just type out your desired project directory tree to start.

For formal projects, Gliffy is a good option for professional-looking visualization.

Before we can do anything with your project's modules, you will also need to spend some time describing your
project preferences to Cmod by filling out any relevant fields you find in config.txt. There is a more detailed
guide about this here:

After your config.ini file is more customized apart from the default settings, you can generate some C modules
for your project. Cmod will follow your project description in config.ini, and produce ready-to-test
modules that fit your project's coding style and use your preferred unit test harness!

```
./cmod generate --module=moduleA
```

or simply

```
./cmod gen -m=moduleA
```

or more simply, using the recommended bash aliases:

```
gen -m=moduleA
```

This is about as good as it gets for frameworks in the C language. Simple code/file generation will
always have subjective results, so be sure you customize these python functions (.....) until you're happy with
the appearance and names of the generated module files.

Make a child-module (nested module) by specifying a nested path:

```
gen -m=moduleA/subcategory/submoduleA
```

In this case, submoduleA is a separate and distinct module from moduleA, and subcategory is just a directory in between them.
Cmod does not see it as a module. These 2 modules are nested, and that's all. There is nothing more we need to know about them.
There is no dependency chain implied here in this structure, it is just for organizational form. You COULD allow a nested module
structure imply a dependency chain, but there are reasons why this is not typically done.

Things to do with your codebase once it's organized into modules: "Cmod things"

These commands will work with "empty" modules, since Cmod generates a default
test case automatically. So if you don't have your code moved into your module
directories yet, don't worry. Just generate some "blank" modules somewhere if you
just want to experiment with the Cmod command base.

The "help" command should be your go-to when you need a quick reminder of how to use cmod.
It's output was thoughfully arranged to be both optimal and pleasant to read. Please enjoy
using it.

```
./cmod --help
./cmod -help
./cmod --h
./cmod -h
```

The "list" command can be called at any time. All it does is read your project files, and show them in a condensed, helpful way

```
./cmod list                                           -- List out all the modules under the project root directory
./cmod list --module=MODULE_A/module_b                -- List out all the modules under the MODULE_A/module_b
./cmod list --m=my_mod --s=?                          --List all the test suites under the 'my_mod' module
./cmod list --m=my_mod --s=TEST_MY_MOD_SUITE --t=?    - List all the test cases under the TEST_MY_MOD_SUITE in my_mod module
./cmod list --m=my_mod --s=? --t=?  - List all the test suites and their test cases under the my_mod module
```

The "tree" command works identically to the "list" command, but the output is always formatted with a directory tree output style.

The "build" command runs the Makefile in each module, telling Make to compile, and link the module tests, but not to run them.

```
./cmod build --m=module
```

The "report" command can also be called at any time, but it's mostly useful when your modules have test results to show.

```
./cmod report
./cmod report --module=MODULE_A/module_b
./cmod report --module=MODULE_A/module_b --s=TEST_MY_MODULE_B_SUITE
./cmod report --module=MODULE_A/module_b --s=TEST_MY_MODULE_B_SUITE --t=TestMySpecificTestCase
./cmod report
./cmod report
./cmod report
```

The "test" command can be ran at any time. It assumes your test builds compile and run.

```
./cmod test                   -- Build and Run all tests found in the project
./cmod test --m=module        -- Build and Run all tests found in the module
./cmod test --m=module --r    -- Build and Run all tests found in the module, and in all child modules
./cmod test --v=2             -- Build and Run all tests found in the project, reporting the results with a verbosity level of 2. [0-7 are valid]
./cmod test --m=module --suite=MODULE_TEST_GROUP -- Build and Run all test cases found in the module's test group called "MODULE_TEST_GROUP"
./cmod test --m=module --s=MODULE_TEST_GROUP --case=TestMyCaseDoesNotFail   -- Build and Run only the specified test case, requires the module and suite parameters
```


The "stat" command runs a few tools and returns some interesting metrics about your project modules

```
./cmod stat
./cmod stat --m=module
./cmod stat --m=module --r
```

The "tdd" is a quick way to do several things at once, which helps the developer doing Test-Driven Development
It is a quick way to run

```
./cmod build --m=path/to/module
./cmod test --m=path/to/module
./cmod report --m=path/to/module
```

Instead, just use

```
./cmod tdd --m=path/to/module
```

Each build-test-report sequence will occur one at a time in a separate process, for each module specifed:

```
./cmod tdd --m=path/to/module --r
```

OpenProcess:
  ./cmod build --m=path/to/module
  ./cmod test --m=path/to/module
  ./cmod report --m=path/to/module
CloseProcess

OpenProcess:
  ./cmod build --m=path/to/module/submod1
  ./cmod test --m=path/to/module/submod1
  ./cmod report --m=path/to/module/submod1
CloseProcess

OpenProcess:
  ./cmod build --m=path/to/module/submod2
  ./cmod test --m=path/to/module/submod2
  ./cmod report --m=path/to/module/submod2
CloseProcess

If you want to quickly test your entire project, this is probably the fastest way:

```
./cmod td
```

This command also works within any module directory. So I you need to focus your development
attention with only 1 module for a while, just navigate to the module and run:

```
./td
```

This will run the cmod tdd sequence for the local module only - enabling quick and easy TDD cycles.
