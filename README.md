# c-elmelet
Introduction to C++
In this module, we will learn C++, particularly its C++17 dialect. It is a "modern" revision of the language, and mature enough to be used in the industry.

To understand C++ we have to think like a C++ programmer. Knowing its history and philosophy can also be beneficial.

Historical context
C++ started as an extension of the C language to add Simula-like OOP. So just as much as Simula is a "fairly faithful superset" of ALGOL 60, C++ is a "fairly faithful superset" of C.

What we need to take away from that is that we can compile C code with a C++ compiler almost without surprises.

On the other hand, this also means that we can use constructs from C, but we may want to avoid them to write more idiomatic C++.

Additionally, coming from C, it's important to understand that C++ is a language that compiles to executable machine code. The build process requires more involvement, but build tools can hide this from us.

Whenever the C++ language designers had two competing ideas as to how they should solve some problem, they said, "OK, we'll do them both". So the language is too baroque for my taste. – Donald E Knuth

C++ has been around since the 80s and it has grown a lot since then. It is one of the biggest (in scope) languages around. Way bigger than Java or C#. So we shouldn't strive to understand all of it.

Life is too long to know C++ well. – Erik Naggum

During the course, we'll focus on acquiring a good basic understanding of the core principles rather than exploring every keyword (there are around 95, and java has around 68)

How real projects get around, what coding standards are in use, what subset of the language element is in use and what are the best practices.

We'll assemble our own as the course progresses.

Watch out: from C++11 (one of the first modern standards) to C++17 there were some great changes.

There are new best practices (compared to the previous version). Some old keywords got new meanings (i.e. auto used to mean something completely different). Lots of new stuff in the standard library, not just in the language. So when looking up things online always make sure that the advice applies to at least C++17.

Philosophy
C++ has a "zero runtime overhead" philosophy, which means that it doesn't force us to use anything that would come with additional computation costs. No boundary checks at runtime, no garbage collector, etc.

This may sound like we don't get anything from the language. But this is achieved via zero-cost abstractions. These are language features that give the compiler enough information to guarantee there will be no runtime errors. But they can be "compiled away" so that they don't generate additional runnable code.

Here is something to inspire us, what can be achieved if we use these abstractions well: a video that showcases C++17 features.

Conclusion
Let's concentrate more on getting a feel for the language.

It is really hard to find good starting points. Here are some sources we will use during the course and our career as a C++ developer:

The c++ reference is very explicit about what is C++ and very reliable
C++ reference Another generally used wiki about every library and version of C++
Frequently Asked Questions on the committee page
Thematic gotchas Bjarne's homepage
C++ General Guideline
Task:
Complete the following Lessons on codecademy:

Hello World
Hello World Lesson
Hello World Article
Compile & Execute Lesson
Compile & Execute Article
Variables
Variables Lesson
Conditionals & Logic
Conditionals & Logic Lesson
Logical Operators Lesson
Loops
Loops
Errors
Vectors
Vectors Lesson
Arrays Article
Functions
Functions Lesson
Code Challenge: C++ Functions
Functions: Scope & Flexibility
Classes


CLion, our new IDE
CLion, our new IDE
CLion is the C/C++ Integrated Development Environment produced by JetBrains. It looks and feels very similar to Idea. Editing works pretty much the same way too.

Build tool
CLion uses CMake as a build tool. It comes bundled with it. As of now, we don't have to care about it much. It will be discussed at a later week. But if we look into CMakeLists.txt it is easy to decipher.

Debuggers
There are many ways to debug a C++ application There are debuggers that can be used in different IDEs: for example builtin gdb (Gnu debugger) and builtin lldb There are also external debugger tools, we skip them for now.

What is the difference between GDB and LLDB? GDB is part of the GNU framework and was created to work alongside g++, the GNU C++ compiler. LLDB is part of the LLVM framework and was created to work alongside of clang++, which is the LLVM C++ compiler. Ideally, you would use the debugger of the same framework the compiler is part of.

You might raise the question what are g++/gcc and clang++? Well, there are multiple compilers for a C++ source code. Let’s say for now they compile the same source code into machine code through a bit different processes.

At the top level, we say GDB is the debugger of the GNU compiler toolchain, while LLDB is the debugger of the LLVM compiler toolchain.

They are similar feature-wise. Choose any of them. You do not have to understand the fine details now (maybe in a few years).

Linter / analyzer
There is clang-tidy bundled with CLion. It is used to find parts in the code that either:

might cause problems in the future
can be done in a more idiomatic way
This is what you need to know to get started and answer questions on the first run. If you want to know more, then here is the official quickstart guide.

Package manager
Managing packages is one of the essential things if you are learning programming, you will meet many different libraries. In industry, we do usually set packages once for every project and use those for months. But it is still essential to keep these packages up to date. C++ was one of the languages that had some lack in this field. The industry and the community felt this should be resolved to make life easier for the developers and not lag behind other languages (like Java’s Maven or Gradle or C#’s NuGet). A couple of package managers raised in the last couple of years. Like the following:

vcpkg - developed by Microsoft
Conan - C/C++ open source package manager governed by a community of developers
We will use vcpkg for now. Clion has support for vcpkg

Coding Style
Set your coding style to Google in the ide: Go to Setting/Preferences | Editor | Code Style | C/C++ then click the button "Set from..." in the top right and select "Google." (thanks to stackoverflow) Or image:
Coding stlye

Footnotes:
If we want to use our own gdb, make sure it is compiled with MI support.

Functions, references
About functions.. What?! But you know the functions already!
Yepp, that's true but anyway read this tutorial and you may notice there are new bits of information hiding here:
https://cplusplus.com/doc/tutorial/functions/

After reading the tutorial, you should be able to answer the question about the difference between arguments passed by value and by reference. This is very important to know and understand. Also, you will know about function declarations, inline functions, and const references. And recursivity. :)
https://x.com/MIT_CSAIL/status/765611108166053888?mx=2

Some reading about references (you do not have to dive into pointers.
https://isocpp.org/wiki/faq/references
For now, the first 3 answers will be sufficient. We will come back to this later) Simply put, references are nothing else than aliases of another variable. Something like google.com is an alias for eg: 142.250.191.46 IP address

Default initialization of variables & initializer list
Default initialization of variables
TL:DR: default initialization rules are very complicated in C++ but it's easy to make your life simple: always initialize your variables!

An article to get a grip on the subject and the usual cppreference page.

It's good to know that local variables have indeterminate values if not initialized and what happens with POD (stands for Plain Old Data - that is, a structure (whether defined with the keyword struct, or the keyword class) without constructors, destructors, and virtual members functions) and class objects (non-PODs constructor is executed if it is available).

And again: don't forget the ancient Indian saying:

"Always initialize your variables Geronimo!"

Initializer list
No it is not the class! This is just the other side of the initialization scheme that is good to follow when you define your custom structure (struct or class)

Let’s dive into it. In short, this is the standard way to initialize members. This mechanism will do the same thing that we discussed above. Your members won't be initialized to a default value, instead you directly call their constructors.

class Actor {
 public:
 Actor(std::string name) : name{name},  hp{10}, damage{2}{};


 private:
 int hp;
 int damage;
 std::string name;
};
If we just use the old version (that you used in Java too)

class Actor {
 public:
 Actor(std::string& name) {
   this->name = name;
   hp = 10;
   damage = 2;
 };


 private:
 int hp;
 int damage;
 std::string name;
};
Is more verbose and here we use the assign function and not the constructor of the objects.

There are a few cases in which you cannot assign value to member variables in the constructor.(source)

When the member variable is const.
When the member variable is an instance of a class without a default constructor.
When the member variable is a reference (same reason as above)
Initializing base class
