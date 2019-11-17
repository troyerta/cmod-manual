# A Review Of The Test-Driven Development Ecosystem For Embedded Systems

In the research world, it's mandatory to provide an in-depth tour or "literature review" of previous work done in the field of interest. But in the open source world, this practice may take a more abbreviated, pragmatic approach which aims to place a contribution into a meaningful context and to acknowledge those who provided the knowledge and resources you used to develop your own work.

In this spirit, I have compiled an abbreviated list of resources that have not only taught me, but will also add contextual value to the reader of this guide. In fact, this Cmod guide is best understood by those who have already had time to chew on these resources for awhile.

## Names to Know in the Embedded TDD Space:
[James Grenning](http://blog.wingman-sw.com/) - One of the original authors of the Manifesto for Agile Software Development (he knows a lot more than you do) Get to know him in these [embedded.fm](https://embedded.fm/) interviews [30](https://embedded.fm/episodes/30), [109](https://embedded.fm/episodes/109), [270](https://embedded.fm/episodes/270)

[Mark VanderVoord](http://www.throwtheswitch.org/) - Author/Face of Unity and Ceedling. Interviewed [here](https://embedded.fm/episodes/103)

[Matt Chernosky](http://www.electronvector.com/) - Author of the ElectronVector blog

## Articles and Blog Entries:

[Phillip Johnston's](https://embedded.fm/episodes/290) (Embedded Artistry's) [Collection of Unit Testing Resources](https://embeddedartistry.com/blog/2018/10/18/embedded-systems-testing-resources/)

[Starfish Medical](https://starfishmedical.com/blog/automated-unit-testing/
)

## Books:

[Test-Driven Development for Embedded C](https://www.amazon.com/dp/193435662X/ref=cm_sw_em_r_mt_dp_U_7Fg0Db497VYS3) by [James Grenning](https://embedded.fm/episodes/30)
\([2](https://embedded.fm/episodes/109), [3](https://embedded.fm/episodes/270)\)

[Embedded Testing with Unity and CMock](http://www.lulu.com/spotlight/mvandervoord) by Mark VanderVoord

[A Field Manual for Ceedling](http://www.electronvector.com/a-field-manual-for-ceedling) by Matt Chernosky

## Courses and Training

[By James Grenning](https://wingman-sw.com/training)

[By Mark VanderVood and Friends](http://www.throwtheswitch.org/dr-surlys-school)

## Test Harnesses

A test harness is a software library that provides and API for writing tests and test suites for software modules. I've listed out the C test harnesses I've found to be appropriate for the embedded systems space.

[Unity](http://www.throwtheswitch.org/unity) - A very popular harness by [Mark VanderVoord](https://embedded.fm/episodes/103)

[MinUnit](http://www.jera.com/techinfo/jtns/jtn002.html) - A minimal harness described by Jera Design, as an example of a simple DIY harness.

[Greatest](https://spin.atomicobject.com/2013/07/31/greatest-c-testing-embedded/) - A "header-only" ANSI C harness made for embedded SW by Scott Vokes over at Atomic Object.

[Catch2](https://github.com/catchorg/Catch2/blob/master/docs/tutorial.md) - A very popular and well-loved test harness. I see if often used for C++ projects, which doesn't exclude from the embedded systems space at all. While I've not seen it used in an embedded system project, there is no reason why it wouldn't work. Is it the best fit? I can't say. But I can say it feels wrong to not mention it due to it's popularity.

[FFF](https://github.com/meekrosoft/fff) - A header-only function mocking harness by Mike Long. This is my preferred mocking harness [over CMock](http://www.electronvector.com/blog/cmock-vs-fff-a-comparison-of-c-mocking-frameworks).

## TDD Frameworks

If a Test Harness is software that provides an API for writing tests, then Test Frameworks are software tool that assist with building test code, running test software, and collecting results.

You could say a Test Framework is a "test harness with a front-end" or a test harness with batteries included. Test frameworks typically provide a test harness along with helper tools and scripts that define a TDD cycle. Frameworks tend to imply (impose?) a specific workflow on your software development process.

As a more general rule, if you have to "install" something on your development PC to use it, it is probably more of a test framework than a harness.

[Wikipedia List of Unit Testing Frameworks](https://en.wikipedia.org/wiki/List_of_unit_testing_frameworks#C) - A sort-of helpful list of test frameworks sorted by language. A number of the list items includes frameworks that are proprietary/closed-source, or are unsuitable for a embedded firmware project.

[Cpputest](https://cpputest.github.io/) - This framework was primarily authored by James Grenning, our ascendent master of the embedded TDD world. It is written in C++, but supports tests written in C. It is xUnit compatible and includes a Unity-like test harness with mocking support and automatic test runner generation.

[Ceedling](http://www.throwtheswitch.org/ceedling) - A prominent ruby gem by Mark VanderVoord, Mike Karlesky, and Greg Williams at [ThrowTheSwitch](http://www.throwtheswitch.org/). Ceedling uses the Unity, CMock, and CException test harnesses all at once. It also includes a build system with automatic test runner generation. There are many tutorials and articles written about the use of Ceedling.

[CMocka](https://cmocka.org/) - I know little about this framework, but it claims to be suitable for embedded systems. The ThrowTheSwitch crew says the framework is "pure C", and also less "scripted" - which is interesting considering what Cmod is.

## Summary

Is this the entire extent of the Embedded TDD world? Absolutely not.

Do I think the reader of the Cmod Guide needs to see much else? Probably not. Let's get started exploring Cmod as a *Modularity Framework* and what that means going forward.
