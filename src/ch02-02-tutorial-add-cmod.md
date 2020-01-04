### Add Cmod to the Project

If you're convinced there's no magic happening here, then let's add Cmod to our demo project.

Clone Cmod somewhere nearby our demo project:
```shell
$ git clone https://github.com/troyerta/cmod.git cmod
```

### Examine Cmod

Looking inside the cmod directory, we see the following:

FIX
```shell
$ cd cmod && tree
cmod/
|
├── cmod
└── tools/
    └── cmod/
        ├── python_file.py
        ├── another_one.py
        └── ..
```

Apparently, Cmod is just a collection of Python scripts and classes.

Now that we have both the cmod sources and a demo project, let's add Cmod to the project. In this case, the simplest way to achieve this is to copy the "**cmod**" file and the entire "**tools/**" directory to our project's root directory.

Make sure your demo project now looks like this:
```shell
$ tree
cmod-demo/
|
├── foo/
|   ├── foo.c
|   └── foo.h
├── bar/
|   ├── bar.c
|   └── bar.h
├── main.c
├── cmod
├── Makefile
└── tools/
    └── cmod/
        ├── python_file.py
        ├── another_one.py
        └── ..
```

### Build Cmod's Virtual Environment

Lastly, we'll make a Python3.8 Virtual Environment *in* our demo project. It will contain the Python executable *for this project*.

**Why would we want to do this?**

Python's *virtual environment* feature actually builds and locally stores an *instance* of Python 3.8 as an executable binary in some directory you specify. This prevents your coworkers and collaborators from having to use identical Python installations and Host Operating Systems on their development PCs.

This has a couple negative consequences to note:

The virtual environment must be deleted and then remade each time the project directory is moved or copied to a new location on disk.

The exact mechanisms are not anything to mind, just run cmod venv to rebuild your venv at anytime.

Build the cmod venv so that we can keep our use of Python local to the project. (Be sure to use the exact paths specified here)
```
$ python3.8 -m venv tools/cmod/venv
```

Anytime you make a venv, be sure to add the venv directory to the .gitignore list if you are using git to track your project.
```shell
$ echo 'tools/cmod/venv' >> .gitignore
```

### Test Cmod

Mark the cmod file as "executable". This is the main entry point for any Cmod command we invoke.

```
$ chmod 774 cmod
```

Test the Cmod executable.
```shell
$ ./cmod help
```

Given the "help" command is working, we note a few interesting things about Cmod:

- Cmod gets "integrated" into a project, not installed to your computer
- Cmod will not add environment variables to your PATH, and won't copy itself to your system directories
- Cmod is not made "for" Unix, Windows, or OSx - it's made for your project
- Cmod lives with your project.
- Each instance of Cmod can be modified to suit the special needs of it's host project

### Invoking Cmod

When you run Cmod to do "module things", the "cmod" file is what you execute.

```shell
$ ./cmod <command>
```

A file is normally executed with "./" on Unix systems.

For commonly-used scripts, it can be nice to add an alias to your terminal to shorten the invocation command.

A good alias to start with is abbreviating ./cmod to just cmod.

This can be done by adding the following to your .bashrc:

.bashrc:
```
alias cmod='./cmod'
```

Now you can invoke cmod by with a slightly simpler command:

```shell
$ cmod <command>
```

Additional aliases will be suggested later in the tutorial.

### Summary

To recap, this is all we've done so far:

- Add Cmod files to a dumb sample project
- Setup cmod's Python virtual environment
- Ran ./cmod help too make sure the cmod venv works
- Added a simple "./cmod" alias
