
### Download The Demo Project

To start, download the dumb sample project and save it to your favorite sandbox directory, and call it "dumb_sample_project". This project is just for show - not a recommended way to start a project.

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

- If you're not using GCC, just go into the Makefile and change the CC variable to point to a C compiler you do have installed, or simply 'cc'. If this step is necessary for you, you'll need to do this somewhere else again later - but don't worry, this isn't a barrier to using Cmod at all.

This is the more important point:

"Always start from a working place"

Great. So this C project is a "real" project, and is convincingly minimal. Nothing unusual going on here. Heck, if you want to delete the Makefile and build and run this sample program with your own tools, go for it. Cmod doesn't care about your cross compiler - it just needs an ordinary, general C compiler.

Once you've convinced yourself that nothing funny is going on here, let's make sure our two **hard** dependencies are installed, and accessible from the terminal. Make sure these two commands work:

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
Still good to go? Great. It's time to add Cmod to our dumb sample project.

Download Cmod from here:

Save it nearby the dumb sample project, and call it "cmod".

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

Now that we have both the project and the cmod directory, can now merge the two projects together. In this case, the simplest way to achieve this is to copy the "cmod" file to the sample project root directory, and copy the entire "tools/" directory and it's contents there as well. Don't worry about copying the requirements.txt file if you don't want to. But it won't hurt anything if you do.

```shell
$ cp cmod/cmod dumb_sample_project/cmod
$ cp -a cmod/tools/. cmod/dumb_sample_project/tools
```

You should have the resulting project:
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

Lastly, we'll make a Python3.8 Virtual Environment *in* our dumb sample project. It will contain the Python executable *for this project*.

Do this by running the following: (Be sure to use the exact paths specified here)
```shell
$ python3.8 -m venv tools/venv
$ source tools/venv/bin/activate
$ deactivate
```

If you are planning to make this project, or one like into a track git repository, be sure to add the venv to the ignore list. You will not want to track this directory, since it is partly dependent on your PC. Your teammates will surely not want to use your venv either, they will use their own untracked venv when they develope in the project using Cmod.

```shell
$ echo 'tools/cmod/venv' >> .gitignore
```

```shell
$ gcc --version
gcc (Debian 6.3.0-18+deb9u1) 6.3.0 20170516
Copyright (C) 2016 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

Assuming you got no error messages along the way, you should be ready to use Cmod.

To recap, this is all we've done so far:

- Add Cmod files to a dumb sample project
- Setup cmod's Python virtual environment
