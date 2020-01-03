### Add Cmod



### Build the Demo Project

If you have Make and GCC installed, give it a try:
```text
$ make
```

```text
$ ./main
```

Of course, you can modify the Makefile to call a different C compiler if you find it necessary to do so. Luckily, Cmod doesn't care about the C compiler you choose the use.

This is the more important point:

"Always start from a working place"

Overall, we find that this project is convincingly minimal. There is nothing unusual, or exceptional going into this project. Heck, if you want to delete the Makefile and build and run this sample program with your own tools, go for it. Cmod doesn't care about your cross compiler either - it just needs an ordinary, general C compiler.



### Add Cmod to the Project

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

### Build Cmod's Virtual Environment

Lastly, we'll make a Python3.8 Virtual Environment *in* our dumb sample project. It will contain the Python executable *for this project*.

**Why would we want to do this?**

Python's *virtual environment* feature actually builds and locally stores an *isolated instance* of Python as an executable binary in your target directory. This prevents your coworkers and collaborators from having to use identical Python installations on each of their development PCs (all of which may be running different operating systems). Downloading and developing a project no longer affects the system-wide instance of Python, while syncing the versions of Python and any modules used to each developers instance of the project.

This has a couple negative consequences to note:

The virtual environment must be remade each time the project directory is moved or copied to a new location on disk. This is because the system installation of Python and the project's instance of Python need to track each other to allow the system-wide instance to modify the project instance, and make system-wide resources available to the project instance.

The exact mechanisms are not anything to mind, just run cmod venv to rebuild your venv at anytime.

Do this by running the following: (Be sure to use the exact paths specified here)
```shell
$ python3.8 -m venv tools/cmod/venv
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

### Summary

To recap, this is all we've done so far:

- Add Cmod files to a dumb sample project
- Setup cmod's Python virtual environment
