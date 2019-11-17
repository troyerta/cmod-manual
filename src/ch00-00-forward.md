# Forward

The argument for software quality was made long ago, by people far wiser and battle-hardened than I.

As such, this is not the space to be making the argument for ideas I didn't invent.

The entire project was driven by the need for an improved Test-Driven Development (TDD) framework for embedded systems development. While the core functionality of Cmod has evolved into a tool for a discipline *parallel* to TDD instead, the mention of TDD in this guide is frequent.

To be working and learning in this industry is an incredible experience, and having an opportunity to contribute to a world-changing industry is a privilege I hold with weight.

If you're like me, then you might be a slow learner. It took much time with some talented educators and mentors for me to understand the true power and potential of mathematics while in school. It took time for me to grip the long handles of linear systems, feedback design, and computation. I never really had moments when things suddenly "clicked" into place for me. Though, when these did become clear, they sometimes changed everything.

Cmod is a small outpouring of excitment I experienced when I was learning about Test-Driven Development while reading James Grenning"s excellent book: Test-Driven Development for Embedded Systems. It made sense right away. Well. Shortly after I tried the work, that is. I became filled with a stark realization that most of the embedded software I've encountered is not written by the guidance of well-written tests. After reviewing the landscape of available tools and frameworks for TDD for embedded systems, it was became more obvious why this was the case. Things in this space could be better. They could be improved. So I took some to learn a new language to build a tool to help solve this problem. I shaped it, refactored it, and hammered it into something I actually enjoyed using, and I hope you will enjoy using it too.

## What is Cmod about?

If you were given the task of writing an implementation of the standard C library's memcpy() function, how long would it take you? Could you develop an implementation in a minute or two?

Now, suppose you learned that this function would be running in a complicated system that will carry human lives from Earth to Mars and back again. That if your software messes something up, human lives will be put in danger.

Now how would you implement memcpy?

Cmod tools are all about *confidence*: no matter your level of experience. Cmod tools enable you to build complex projects with sanity and structure.

## What Is The Scope Of This Guide?

This book is about more than the Cmod tool. It is an exploration of embedded software design. The CMod tool is my humble suggestion submitted on the side, that demonstrates ideas and disciplines that can be done without ANY special tools. This is my 2 cents chipped into the embedded software design space.

\- Tyler Troyer
