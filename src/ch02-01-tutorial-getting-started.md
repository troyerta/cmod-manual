# Getting Started

### Clone the Demo Project

To start, download the dumb sample project and save it to your favorite sandbox directory. You can call it "dumb_sample_project" or something similar. We'll use this directory for demonstration purposes only, so feel free modify like it any way you like.

Now note the Demo Project's contents:
```text
dumb_sample_project/
|
├── foo/
|   ├── foo.c
|   └── foo.h
├── bar/
|   ├── bar.c
|   └── bar.h
├── main.c
└── Makefile
```
Some observations:
- We have a main source file
- We can see two C modules: "foo" and "bar"
- Given the Makefile, we assume we can build the project with GNU Make.

### Get started:

Clone the Cmod demo project into a directory called "cmod_demo":

```
$ git clone http://github.com/troyerta/cmod_demo cmod_demo
```

Start by navigating to the demo project directory:

```
$ cd cmod_demo
```

This demo is just the cmod scripts included with some default config settings.

Build the cmod venv so that we can keep our use of Python local to the project.
```
$ python3.8 -m venv tools/cmod/venv
```

Make sure cmod works: (make sure the "cmod" file is executable)

```
$ chmod cmod 774 && ./cmod help
```

Given this is working, notice a few interesting points about Cmod to note:

- Cmod gets "integrated" into a project, not installed to your computer
  - Cmod will not add environment variables to your PATH, and won't copy itself to your system directories

  - Cmod is not made "for" Unix, Windows, or OSx - it's made for your project
  - Cmod lives with your project. This ensures portability of your projects across teams of developers and whatever operating systems they choose to develop on.

- Each instance of Cmod can be modified to suit the special needs of it's host project