# Getting Started

### Clone the Demo Project

To start, clone the Cmod demo project into a directory called "cmod-demo". We'll use this directory for demonstration purposes only, so feel free to place somewhere disposable.

```shell
$ git clone http://github.com/troyerta/cmod-demo cmod-demo
```

Start by navigating to the demo project directory and not the contents:

```shell
$ cd cmod-demo
$ tree
.
├── bar
│   ├── bar.c
│   └── bar.h
├── build
│   └── main.out
├── foo
│   ├── foo.c
│   └── foo.h
├── main.c
├── Makefile
└── README.md

3 directories, 8 files
```

CONTINUE

Some observations:
- We have a main source file
- We can see two C modules: "foo" and "bar"
- Given the Makefile, we assume we can build the project with GNU Make.

### Get started:



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