
# Assumptions & Requirements

Cmod has two **hard** system Requirements:

1. Python 3.8x

2. GNU Make

That's it.

Cmod stands in a unique place among other development tools;
it is not "installed" to your PC in the traditional sense. Instead, Cmod gets "integrated" into a project.

Cmod will not add environment variables to your PATH, and won't copy itself to your system directories. It lives in your project as a part of your project. This retains the portability of your project across teams of develepers and their host operating systems. Cmod is not made "for" Unix, Windows, or OSx - it's made for your project.

#![Body frame](giphy.gif)

Cmod's requirements are both few and widely popular as tools in the embedded software space already.

This is significant because the tools in this niche space of "embedded systems software development frameworks" (such as those mentioned on the previous page) are arguably inappropriate for embedded SW development in the first place.

## Why Not C/C++?

Let's sum this up much faster. Don't poop on the other frameworks.

First, CGreen and Cpputest are written in C and C++ - or some unholy mix of the two. Is this the obvious choice for a test framework? Let's see what these tools' documentations have to say about it:

From the Cgreen Docs - Page 1:

"Unit tests are written in the same language as the code, in our case C or C++. This avoids the mental overhead of constantly switching language, and also allows you to use any application code in your tests."

Hmm. It's hard to tell if the point being made here is about the *tests* being written in C/C++, (Which is just super common and normal) or if the point is about the *test framework* being written in "the same langugage as the tests" (which not an obvious productivity advantage in the case of C/C++).

Let's take a look at what Cpputest has to say about it's authored language from the Cpputest main webpage:

"CppUTest is a C/C++ based unit xUnit test framework for unit testing and for test-driving your code. It is written in C++ but is used in C and C++ projects and frequently used in embedded systems.

CppUTest’s core design principles

- Simple to use and small
- Portable to old and new platforms
- Build with Test-driven Development in mind"

While it's probably true, that the test binaries of Cpputest compile down to nice and small images, a singular glance at the main repository for the project makes one wonder how *simple* the framework actually is.

It *looks* like there is quite a lot going on there in the project files, and so as soon as the project tests stop building or translating correctly to a new machine, or when the on-host packages and libraries need to change, the new problems presented to the developer are going to *look* like new headaches. It's probably not easy to *debug* this framework as soon as it doesn't work for you. It's likely best if the developer is intimate with C++ to start with.

Should this actually be a requirement for the embedded C developer?

Are there more general reasons we should be wary of using a test framework written in C/C++?

Weak wording - doesn't make the point
3. C/C++ needs to be compiled - which means there is more of an implicit runtime environment assumption made on the development machine. This can mean that test framework requires specific libraries to be installed on the development machine - which you typically need to hunt down and install yourself.

4. Marrying your test code to the test framework is probably a bad idea for longevity and maintainability.

5. Test Frameworks can essentially add a specialized build system to your project. This is more for the developer to learn, and becomes yet another unique dependency that gets stapled onto the project. Do you need to use CI servers to test and deploy your project? Would you rather your entire codebase be testable using few, very common tools? Or would you rather be dependent on rather specific distributions of C libraries you don't maintain yourself?

There are some takeaways from this to be considered:

1. If you're going to essentially add a new build system to your codebase to support TDD and Unit testing, you should be intimately familiar with the authored language of the *test harness* you are using, and very comfortable with the language and build process of the *test framework* you adopt. This quickly becomes a good case for using a home-grown test harness with a dirt-simple build system. But this is not the only way to achieve our goals. The alternatives however, do require the extra study and understanding of new tools that continually hold your attention away from *writing tests*.

## Why Not Ruby?

Next, we should consider Ceedling and it's dependencies. Ceedling is a Ruby gem, and can be installed very quickly - if your Bundler installation doesn't get confused along the way. Ceedling is also good at adding instances of itself to your sandbox, but it's hard sell to ask the embedded C developer to adopt and learn the included 'Rake' build system.

Rake gives you a 'rakefile' to work with, but you really need to know how it works before you can use it in a production setting. This would best be done by learning Ruby.

At this point it is worth asking a few questions.

"Why is my C test framework written in Ruby?"

"Does Ruby have a long history of being an especially close friend of the C developer?"

"How about the embedded C developer?"

Is there another way?

## Why Python 3.8x?

If you had a choice to build a productivity tool for youself, would you choose C? C++? How about Ruby? Of course not. If you've haven't been living under a rock, you might likely choose Python.

## Why GNU Make?

- Make is a bare-minimum development utility already installed on most development machines.

- Make is straightforward and transparent about how it builds and links your tests - so they can be understood again later and understood by other developers now

- Using Make encourages a simple runtime environment your test build, and makes your dependencies obvious

- Easy to move your tests to a specific toolchain

- Easy to export and ship code modules as independently testable by simply including it's tests and a Makefile - true portability

- Easy for another developer to build somewhere else

- Doing TDD should be the focus of your attention, so your development environment should easy to understand and repeatably simple to port to another development machine..

Cmod's **soft** requirements are things like a working bash-like terminal, and a host system C compiler accessible from the terminal (typically GCC).
