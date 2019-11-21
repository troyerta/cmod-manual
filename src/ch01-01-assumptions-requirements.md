
# Assumptions & Requirements



### Assumptions About the Reader

- A working knowledge of C and the build process for C programs

- Ability to navigate a PC through a command-line interface

- An interest in improving the embedded software

### System Requirements

Cmod has two **hard** system requirements, and one *soft* requirement:

- **Python 3.8x and GNU Make**

- *A C compiler* for the development PC - accessible from your system path

That's it. Again, these are the system requirements, not the user requirements. You don't *have* to know anything about Make or Python. But it's recommended that you do. After all, Cmod is just a collection of Python scripts that call Make in special ways.

This implies a number interesting facts about Cmod:

- Cmod gets "integrated" into a project, not installed to your computer
  - Cmod will not add environment variables to your PATH, and won't copy itself to your system directories

  - Cmod is not made "for" Unix, Windows, or OSx - it's made for your project
  - Cmod lives with your project. This ensures portability of your projects across teams of developers and whatever operating systems they choose to develop on.

- Each instance of Cmod can be modified to suit the special needs of it's host project

- Cmod is C-compiler agnostic - as long as your development PC can run the resulting executable, the compiler used does not matter

- Cmod is OS-agnostic - it does not matter if you develop on Windows, Linux, or on OSx

- Cmod lets you to write your tests in a delieverable way - the output of your TDD efforts are modules that come with test suites that can be built and ran be any basic C compiler, no dependencies on specific libraries. Cmod can even generate a complete Makefile for you, so you can always package and ship your code in a form that can be tested anywhere,

```text
#![Body frame](giphy.gif)
```

## Why GNU Make?

- Make is a bare-minimum development tool already installed on most development machines

- Make is straightforward and transparent about how it builds and links your tests - so they can be understood again later and understood by other developers now

- Using Make encourages a simple runtime environment for the test build, and makes your dependencies obvious

- Easy to move your tests to a specific toolchain

- Easy to export and ship code modules as independently testable by simply including it's tests and a Makefile - true portability

- Easy for another developer to build somewhere else

- Doing TDD should be the focus of your attention, so your development environment should easy to understand and repeatably simple to port to another development machine..
