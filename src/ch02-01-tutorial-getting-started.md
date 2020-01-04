# Getting Started

### Clone the Demo Project

To start, clone the Cmod demo project to a directory called "cmod-demo". We'll use this project for demonstration purposes only, so feel free to save it somewhere temporary.

```shell
$ git clone http://github.com/troyerta/cmod-demo cmod-demo
```

After cloning, navigate to the demo project directory and note the contents:

```shell
$ cd cmod-demo
$ tree
.
├── bar
│   ├── bar.c
│   └── bar.h
├── foo
│   ├── foo.c
│   └── foo.h
├── main.c
├── Makefile
└── README.md

2 directories, 7 files
```

Some observations:
- There are two C modules: "foo" and "bar"
- We have a main source file
- Given the presence of a Makefile, we assume we can build the project with GNU Make.

### Examine the Program

Opening the project with your favorite code editor, you'll see how the demo program is organized and what it does.

The main program simply calls functions from the "foo" and "bar" modules, telling us that they are compiled and linked correctly.

Looking into the Makefile shows us that any .c sources down to 4 directories deep will be compiled and linked into the program.

Lastly, one of the Makefile's rules will run the program after the compiling and linking with GCC.

### Build and Run

If you have Make and GCC installed, go ahead and give this a try:
```shell
$ make
Hello world!
Foo!
Bar!
```

Of course, you can modify the Makefile to call a different C compiler if you find it necessary to do so. To Cmod, it doesn't matter which C compiler you build the application with. But for this demo, there no reason to assume that Cmod can't use GCC as well.

If you had to change the compiler in the Makefile to build and run the program successfully, take note. You will need make a similar adjustment later in this tutorial.

Building an running a Makefile-based C project like this is all basic stuff if you understand the how to build C programs already. The point of this step was to convince you that you've started from a "working place" going forward, as a test of our tools. If you would rather delete the Makefile and build the demo program with your own tools, go for it. Cmod doesn't actually care about how you build your application. We'll see why in later steps.
