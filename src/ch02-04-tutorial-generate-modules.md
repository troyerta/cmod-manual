# Generate C modules

Let's start by generating an instance of Cmod's first-class citizens: a C module.

Use this command to generate an example "accelerometer" module: Read the output before pressing "ENTER"
```
$ cmod generate --module=accel
```

Cmod shows you a preview of the files it's planning to generate for your module.

Each of the filenames and filepaths shown in this preview are configurable, and can be changed suite your project's naming scheme, organizational requires, or any additional preferences. See "Module Configuration" for details.

If you messed up your module's name, you have a chance to cancel the operation by pressing "n" for "no".

Press "ENTER" from here to make your module.

Using your favorite IDE, examine your new module's contents. You'll see that a module is just a directory with a templated arrangement of C sources (.c) and headers (.h). This means that distinguishing a directory in your project from a module becomes a little tricky. We need some way to mark each module directory as distinct from other project directories.

Cmod's default solution is to identify any directory with a "unit_test" directory within it as a module. The identifying marker file or directory can be configured as anything else, since there are plentry of reasons why the default marker may not suit your project. See "Module Configuration" for details.

Since the module we just created contains this marker, cmod can find the "accel" module anytime we need to perform module tasks in our project. You can confirm that Cmod is aware of your module:

```
$ mkdir not_a_module
$ cmod list
```

You'll see that cmod will ignore any directory that does not contain the module marker.



Cmod's module awareness works for nested modules too, generate some additional modules before continuing:
```
accel/lism43566d

wifi

graphics/primitives/circle

graphics/primitives/rectangle
```
While Cmod commands are memorable and tend to be complete words specifying actions, they can still be a mouthful to type each time. You can use "$ cmod gen -m=module_path" if you prefer to be brief. See "Cmod Command Aliases" page for variations of each command and tips for calling into cmod with brevity.

Note that the modules we created are named by the deepest directory in the path we specify. This means that "circle" and "rectangle" are modules, but "primitives" is just a directory. This also means that the lism43566d module just happens to live in the accel module, treating it like just another directory. The two modules actually have little to do with each other, with is a favorable property of modular code. In this case, it could make sense to nest these two modules in the name of organization. We could choose to never use nested modules by simply moving them all to the project directory for a flat project structure, or just generating them there in the first place. Cmod does not care about how your choose to organize your project.

Now list out your modules again to confirm "primitives" is not a module:
```
$ cmod list
```

If you want to be more choosy with the modules to look for, you can specify a different root module to search from:

```
$ cmod list --m=graphics
```

While it may be nice to get lists of modules, this command is not very useful to the software developer. Understanding this command gives insight to how Cmod sees and manages your project.

Projects often contain a mixture of directories containing source code, libraries, tools, scripts, and documentation. Cmod includes a more useful command that lets you view your project's modules, along with the relationships between them. Think of it as way to filter out anything that isn't managed by Cmod.

```
$ cmod tree
```

Just like with the list command, you can specify a different root module to draw the tree from:

```
$ cmod tree --m=graphics
```

One nice thing about the Cmod interface is the carry-over of flags used for each of the commmands. Specifying a module with "--m=" applies a command to a single module. Adding the "--r" flag applies the command to the specified module, and any modules under it, recursively. Leaving out the "--m=" command applies commands to the entire project.