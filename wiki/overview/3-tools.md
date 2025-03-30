# The Tools of Software Engineering

## What Are the "Tools of the Trade"?

![Software engineering tools overview](./resources/Software%20Overview.drawio.png)
*Overview of Development Tools. Note that the specific tools given are only examples - others tools of the same kind exist and in some cases you may prefer them, so look around. These are good tools to start with, though.*

To program anything, you'll need to select a programming language and an Integrated Development Environment (IDE). Programming languages allow you to express your intent to the computer, as well as to the next programmer to read your code (this latter point is just as important at the former point, if not more important). IDEs are all-in-one applications that contain a text editor (for writing the code itself) and quick and convenient access to all the other tools you'll need to create programs. I'll go over some of these tools here too, some of which you may not use until you are further into learning programming.

## Language

Giving an opinion on which language to start to learn programming with is almost guaranteed to cause an argument (hopefully a constructive one). Trying to give comprehensive, objective, and evidence-based reasoning why you're right, while extremely important, will cause more of an argument.

Use **Python**. I have accepted the consequences of these words.

If you want to use a different language for whatever reason, you may still get something out of this walk-through, as it focuses largely on how to design software and manage its development, regardless of the language used to write that software. There will be Python examples, though.

If you really want to know the details of why I chose Python, and you know your way around the programming ecosystem, then see [Appendix 1: Language Choice](./10-appendices.md#appendix-1-language-choice).

## IDE

For an IDE, the current trend is to use Microsoft Visual Studio Code (VS Code or VSC), which has all the tools you need for all the languages you're likely to learn. VS Code is known for being relatively language-agnostic, as it uses plugins to fully support each language. Atom is another IDE that is similar in that regard, though I've never used it.

There also exist IDEs that are more specific to a particular language, such as Net Beans (yuck) or Eclipse specifically for Java, one of the JetBrains IDEs for your chosen language (they make several, including one for Python called PyCharm), Code::Blocks primarily for C++ (though it supports other languages and it's free and open-source if you're a FOSS advocate), and many others. Search the web for "&lt;your language&gt; IDEs" for other options.

Note that, yes, you can technically use Notepad (or Mousepad on graphical Linux, or Nano on the command line), but ***please don't***. This is something of an in-joke within the SE community. Trust me - I'm saving you a lot of pain and misery. Notepad++ (or GEdit on graphical Linux, or Vim/Emacs with plugins on the command line) are tolerable, but you will probably find something more specialised like VS Code much more straightforward and efficient to use.

## Build System

Many languages require you to 'build' your software from its codebase. This broadly means "sticking together the source code, resources, and the full libraries it depends on into a single application", though the details of what this does exactly vary between languages and sometimes even within a language. Usually this involves going through several **stages**, in order, resulting in a runnable program or usable website.

A **build system** is a program and some configuration data that manages all the tasks you need to do in these stages. The program usually comes with a command-line interface, but IDEs often have a graphical (and sometimes automatic or at least simplified) way of configuring and using the build system's program. Build systems generally do at least one of the following:

- **Fetch** dependencies (gather all the libraries listed as dependencies of the software, usually using the relevant package manager - see the Package Manager section for details on what a package manager is/does).

- **Compile** the modules (translate them into a language the computer can understand, plus some other things). Some languages don't require pre-compilation (ie. compiling the software before running it) - in such cases, the language will compile your software for you when it runs.

- **Link** the components (this stage is beyond the scope of this walk-through, as what it does exactly and why it is needed is complicated and largely only important to know about in detail for low-level languages like C and C++). Some languages don't require pre-linking (ie. linking the software before running it) - in such cases, the language will link together the software's parts for you when it runs.

- **Test** the components (running your tests that verify the software does what you think it does - see the Testing section for details on how to do testing effectively).

- **Package** or **Bundle** the codebase (sticking it together and reducing its size so it can be used on other computers, or be served over the internet as a website).

Python does not require you to perform any of the above build stages to run simple programs with no external dependencies (dependencies from the Python Standard Library are not external). This is one of the advantages of Python - building is something you don't need to worry about much.

## Version Control

When creating software, a common problem is managing the changes to the codebase over time. Some common situations in which version control helps you include:

1. If you change your code to make it better, then realise there was something you wanted that you removed while making those changes
2. If you change your code and it breaks something you didn't realise that it would break, so you want to go back to the old version and try again
3. If you want to experiment with multiple ways of solving a problem you're having
4. If multiple people are working on developing the same software at the same time and need to combine their changes into a single copy of the code
5. And more ...

The most effective solution to all these problems is using a version control tool. The most common one at the moment is **Git**. A full tutorial on how Git works is beyond the scope of this walk-through, but this article gives a brief introduction to get you started (I know it's not that brief, but it's as short as I could make it without omitting important things).

## Version Control Hub

While you do not have to use one, a 'version control hub' is a service that hosts your code for you. These services are used for sharing your code, collaborating with others to write and maintain code, and they often provide various other features for product management (like managing tasks, issues, documentation, etc).

GitHub and GitLab are commonly-used VC Hubs.

## Package Manager

I won't go into detail about package managers, as you probably won't need to use one for a while yet, but they are useful to know about. A package is a piece of software that is ready to use. Both 'full' applications and libraries come as packages.
