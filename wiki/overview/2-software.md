# What is 'Software'?

## Who Interacts with Software?

???

## Codebase

Software consists of three main parts: source code, resources, and dependencies.

**Source code** is all the instructions in an application for the computer to do things, as written in a programming language. Programming languages are explained in more detail in the next section.
  - Source code is often split into multiple 'modules', which are independent pieces of re-usable code that inform the computer how to structure data, perform tasks, etc.

**Resources** are things that aren't code, but are used by the code. These usually fall into one of three categories: configuration data, multimedia (images, video, and audio), and user data.
  - Configuration data is data the code uses to control what it does, but that can be changed after the code itself is complete.
  - Multimedia includes images, sound, video, etc. used in the application that is not provided by the user.
  - User data is information and files the user provides, possibly including multimedia. Some modules also include their own resources along with their source code.

**Libraries** consist of modules (code and resources) that can be used by applications and other libraries.
  - Similarly to how a real-world library contains many books that can inform us about a range of topics, a software library contains many modules that inform the computer about various things, such as how to perform a particular task, how to display graphics, the information needed to describe various kinds of things, etc.

The **dependencies** of a piece of software are the libraries that software uses, and therefore depends on being present on the system it is running on to function properly.
  - The dependencies of libraries that your application depends on are called 'indirect' dependencies of your application. As well as not controlling the code or resources of your dependencies, you also do not control which other libraries your application's dependencies depend on.

The **standard library** of a programming language is the set of modules that come with the language that you can use without needing to install anything else. Most languages come with a standard library.

The **codebase** of an application is the combination of that application's source code, resources, and the list of libraries it depends on (but not the libraries themselves).
