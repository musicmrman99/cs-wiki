---
id: vc-installation
---

## Installing Git and How to Run It

If you're on Windows, Git for Windows sets up a basic Unix-like environment for you with git installed. If you're on Linux, just install git through your system package manager. If you're using WSL, then install it like you're on Linux.

Many IDEs will use the 'system git', even if you've installed git in a different way. For Windows machines, the 'system git' is the one installed with Git for Windows. If using VS Code as your IDE, alternatively you can attach it to a running instance of WSL, so if you install git in WSL then you won't have to install Git for Windows outside of WSL.

There are multiple ways of interacting with git, but I suggest you use git on the **command line** (aka. CLI) with the `git` command. This is because IDEs vary in their ability to use all of git's features (most IDEs don't support everything you will want) and some IDEs use undesirable strategies for performing some high-level actions with git. The command line allows you to do everything git is capable of, and to control exactly what git actions to perform to avoid issues.
