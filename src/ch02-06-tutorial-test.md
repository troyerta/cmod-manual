# Test C modules

Another most-important command is the test command. This is your go-to command when running your Test-Driven Development cycles, and when you run you Continuous Integration scripts.

```
$ cmod test
```

Again, try specifying a module to test just that one, then try adding the "--r" flag to test all the nested modules too.

This test command does a lot of things. Cmod is reading the template test source files included in the generated modules, and generating a test runner source file from the tests it finds. It then invokes "Make" on the module's mini-Makefile, taking advantage of the Cmod Makefile found in "tool/cmod/Makefile". This Makefile builds an executable test program, runs it, and then stores the test output in the results text file. Cmod then parses the results file, and reports back the results in the terminal.

For now, this only works "out-of-the-box" with the Unity test harness included with Cmod. If you prefer to use a different harness, refer to the "Supporting a Test Harness" page for details.

Each module's unit test build/run cycle occurs in a new process, so if a module contains build errors, or crashes in a test, the other module tests remain unaffected.

If you're familiar with the Unity test harness, go ahead and add some passing and failing tests to a module and test that module with varying verbosity levels to identify one that you like. You can use values 0-7 here:

```
$ cmod test --m=wifi --v=N
```

Again, if you don't like the test source file name or location, or even the generated code style, remember to review the "Cmod Configuration" page for walkthroughs that demonstrate module customization.

When you find a verbosity level you like, you can set it as the default in the config.ini, so you don't have to specify in the test commadn anymore. You can always specify a new level in the command to override the default. See the "Cmod Configuration" page for descriptions of the verbosity levels.
