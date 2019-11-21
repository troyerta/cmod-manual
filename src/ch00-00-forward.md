# Forward

Cmod is a small outpouring of excitement I experienced when I read James Grenning's excellent book: "[Test-Driven Development for Embedded Systems](https://www.amazon.com/Driven-Development-Embedded-Pragmatic-Programmers-ebook/dp/B01D3TWF5M)". It made sense right away. Well. Shortly after I tried the work, that is.

Reading the book and practicing the exercises within left me with a stark realization that most of the embedded software I've ever seen (and produced myself) was not written by the guidance of well-written tests. My code sort of... sucked.

After reviewing the landscape of available tools and frameworks for TDD on embedded C firmware, it became more obvious why the real-world examples were.. sparse. Things in this space could be better. They could be improved. Current TDD tools were either too specialized or too presumptive. So I took some time to build a tool as my 2 cents towards this problem.

I have shaped the tool, refactored it, and hammered it down into something I actually enjoy using - and I think you will enjoy using it too.

## What is Cmod about?

If you were given the task of writing an implementation of the standard C library's memcpy(), how long would it take you? Could you develop an implementation in a minute or two?

Now, suppose you learned that this function would be running in a complicated system that will ruin human lives if the software experiences an error.

Now how would you implement memcpy?

Still feeling like a pro?

Cmod tools are all about *confidence*: no matter your level of experience, Cmod tools enable you to build complex projects with sanity and structure.

## What Is The Scope Of This Guide?

This book should give you the hope that making quality software for embedded systems is not only possible, but reachable with a little discipline and forethought. This book will make you think about your code before it is even written. It will encourage you to invite form and structure into your codebase, thereby welcoming reliability and maintainence in through the back door. This is an exercise in embedded software architect-ing and project management.

\- Tyler Troyer
