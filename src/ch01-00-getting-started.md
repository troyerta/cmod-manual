# Getting Started

Let’s start our Cmod demo! In this chapter, we’ll do a couple things:

- Download a dumb sample project
- Add cmod to the dumb sample project
- Do TDD in a lightweight, modular, and low-depedency way!

To start, download the dumb sample script and save it to your favorite sandbox directory. This project is just for show - not a recommended way to start a project.

Now note the project's contents:
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
- There are two C modules: "foo" and "bar", and a main source file
- The project build system is GNU Make. You can even build the
  project if you have Make and GCC installed:
```text
$ make
```
- If you're missing GCC, just go into the Makefile and change the CC variable to point to a C compiler you do have installed. If this step is necessary for you, you'll need to do this step again later - but don't worry, this isn't a barrier to using Cmod at all. This is the more important point:

"Always start from a working place"

Great. So this C project is a "real" project, and is convincingly minimal. Nothing unusual going on here. Heck, if you want to delete the Makefile and build and run this sample program with your own tools, go for it. Cmod doesn't care about your cross compiler - it just needs an ordinary, general C compiler.

Once you've convinced yourself that nothing funny is going on here, let's make sure our two **hard** dependencies are installed, and accessible from the terminal. Make sure these two command work:

```text
$ python3.8 --version
```

```text
$ make --version
```
Still good to go? Great. It's time to add Cmod to our dumb sample project.

Download Cmod from here:

Save it somewhere nearby your sample project sandbox.

Looking inside the cmod directory, we see the following:
```text
cmod/
|
├── cmod
├── requirements.txt
└── tools/
    └── cmod/
        ├── python_file.py
        ├── another_one.py
        └── ..
```
See how Cmod is just a bunch of Python scripts and classes?

Open a few of those source files up and examine them if you're not familiar with a Python script.


Ok. Now that we've have both the project and the cmod directory, can now merge the two projects together. In this case, the simplest way to do this is to copy the "cmod" file to the sample project root directory, and copy the entire "tools/" directory and it's contents there as well. Don't worry about copying the requirements.txt file if you don't want to. But it won't hurt anything if you do.

This is our resulting sample project:
```text
my_project/
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

Now there is only 1 more integration step. And while the step is very quick and easy, it deserves some explanation.

Cmod is able to run on your host machine without installing itself to your PC. Instead, Cmod is a tool that you "integrate" to a project. So each project you have is a separate instance of Cmod, and won't interfere with others. This is possible via Python's Virtual Environment module.

We'll make a Python3.8 Virtual Environment *in* our dumb sample project. It will contain the Python executable *for this project*.

Do this by running the following: (Be sure to use the exact paths specified here)
```text
$ python3.8 -m venv tools/venv
$ source tools/venv/bin/activate
$ deactivate
```

Assuming you got no error messages along the way, you should be ready to use Cmod.

To recap, this is all we've done so far:

- Add Cmod files to a dumb sample project
- Build cmod's Python virtual environment
