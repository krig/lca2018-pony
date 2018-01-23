
This talk is either a free horse giveaway, or a talk about a programming language called Pony.

Actually, it's a bit of both! I've got some stickers if anyone wants
one. Not quite a horse, but close. :D

---

So, pony is a relatively new programming language. Development started
some time in 2014, but I only discovered it earlier this
year. It is still pre 1.0. I hope that is clear to everyone coming to
this talk, if not, sorry if that is a bit disappointing. The basic
history of the language is that there used to be a startup behind it
from the beginning, but now it's a community driven effort.

Don't take that to mean that it can't be used for real things,
though. I don't use it for anything real yet myself, but there is at
least one company using it in production in the financial industry. So
although it's still new and changing, pony is a real, usable
programming language.

Okay, so. Not a horse. A BSD licensed, LLVM-based, high performance
actor model-based programming language. Plus some other key features
that I'll get into as we go along.

---

Let's get this part out of the way as well: Why is it called pony? As
I understand it, the reason is basically the saying this quote refers
to.

---

I work at SUSE where I'm the architect for high availability and
mission critical computing. I'm also a programming language geek. I've
played around with creating my own programming languages, and I've
used and still use a lot of different languages both in my current job
and earlier.

However, pony is not yet one of them. I'm also not involved in the
development of pony, other than the occasional pull request. But since
high performance, memory safety and distributed computing are all
really core aspects of what I do, a programming language focused on
these things in particular really appeals to me. Really, I just want
to share my enthusiasm for pony with the rest of you. If it seems
cool, do check it out.

---

In this talk I'm going to try to work from examples as much as I can,
to give you a real feel for what pony is like. There is one core
aspect of pony though which is going to take up most of the time, and
that's the reference capabilities which is how pony ensures memory
safety and data race free concurrent programming, and it's also the
most innovative aspect of pony.

Actually understanding the capabilities takes some experience. I don't
know if I'm completely there yet myself. But it's also my experience
so far that getting the code to compile is pretty easy, and most of
the time you can just ignore it while writing code.

---

The pony project has a website at ponylang.org, and they have a
playground where you can type in and run code directly on the site. So
if you want to follow along and try it immediately without having to
download it, you can use the URL on this slide.

---

If you eventually want to download and install the compiler, it is
already packaged for openSUSE and I suspect that's probably true for
other distributions as well. The ergonomics of using the compiler are
pretty good, the command line tool is called ponyc, and running it in
a directory without arguments compiles any files named dot pony into
an executable named the same as the directory.

There is an early package manager for pony called stable, but I've
never used it myself.

---

OK, enough talking around the language. Here's hello world in pony.

The first line defines an actor named Main. An actor is basically a
single thread of execution. These threads don't map to OS threads but
are more like erlang processes or goroutines in go. The new keyword
defines a constructor, pony is an object oriented language, and create
is the default constructor name but actors and classes can have
multiple constructors.

There are no global variables in pony, so the OS environment with
standard in and out and so on is provided in an environment object
passed to the constructor in an argument.

It doesn't quite look like any other language, but at the same time it
looks like a bunch of languages. To me it looks like there are
influences from C, C++ and Java, but also from Python and
Haskell. And of course the basic actor model design is heavily
influenced by Erlang.

---

Here's a slightly more complete example program.

This introduces classes and interfaces. There's no inheritance, but
there are both structural and declarative interfaces. So it does have
go style interfaces where having the methods corresponding to the
interface is enough.

Pony is garbage collected, but there are some hints of the capability
system here, with the iso and ref annotations for example, and the
consume keyword.

There are packages, the implementation is pretty straight-forward and
similar to Python modules.

Here we actually have more than one actor: Timers is an actor which 

---

OK, so 
