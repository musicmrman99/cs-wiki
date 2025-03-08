---
layout: main
title: Version Control
---

## Installing Git and How to Run It

If you're on Windows, Git for Windows sets up a basic Unix-like environment for you with git installed. If you're on Linux, just install git through your system package manager. If you're using WSL, then install it like you're on Linux.

Many IDEs will use the 'system git', even if you've installed git in a different way. For Windows machines, the 'system git' is the one installed with Git for Windows. If using VS Code as your IDE, alternatively you can attach it to a running instance of WSL, so if you install git in WSL then you won't have to install Git for Windows outside of WSL.

There are multiple ways of interacting with git, but I suggest you use git on the **command line** (aka. CLI) with the `git` command. This is because IDEs vary in their ability to use all of git's features (most IDEs don't support everything you will want) and some IDEs use undesirable strategies for performing some high-level actions with git. The command line allows you to do everything git is capable of, and to control exactly what git actions to perform to avoid issues.

## Configuring Git

After installing git, you should configure some basic settings. Some of the most commonly used settings are explained below, with suggestions about what values to use. See [Common Git Configurations](#appendix-1-common-git-configurations) for some alternative configurations.

1. **Your identity**: Git stores some metadata with each version it creates, including the name and email address of who created the version. You must set the name and email address you want to use for this. If you want to have your code credited to you (which you usually will for professional or open-source work), then use your real name and a professional email address. To set these, run:
   ```sh
   git config --global user.name 'Your Name'
   git config --global user.email 'your@email.address'
   ```

2. **The default branch**: When creating a git repository, git will create an initial 'branch' to create new versions on (don't worry about what these are yet). The default name for this branch is `master` but many people prefer to use `main` or `trunk`. To change the default name to `main`, run:
   ```sh
   git config --global init.defaultBranch main
   ```

3. **External tools**: Git uses external apps for various tasks. The defaults are usually to use `less` as a text viewer, and `vim` as a text editor. `less` is a command-line paginated text viewer. `vim` is a command-line modal text editor. These are the defaults because they are installed in almost all Unix-like systems, but they may be difficult to use for beginners. Whether you want to learn how to use them or swap to a different viewer and/or editor is up to you. To change the editor to `nano`, run:
   ```sh
   git config --global core.editor 'nano'
   ```

4. **Command aliases**: Some common git commands give quite a lot of output by default, and omit some useful details. Various options can be given to those commands to tell them what to output and how to format that output, but these longer commands are difficult to remember. To make longer commands like these easier to use, git supports defining command aliases. Aliases can be run just like any other command (eg. `git repo`). I have found the following aliases to be a useful initial set, though you may want to add your own as you use git more:
   ```sh
   git config --global alias.repo 'log --abbrev-commit --format=oneline --graph --all'
   git config --global alias.repo-l 'log --abbrev-commit --format=oneline --graph'
   git config --global alias.repo-b 'log --abbrev-commit --oneline --graph main..HEAD'
   git config --global alias.repo-d "log --abbrev-commit --oneline --graph --all --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d'"
   git config --global alias.repo-ld "log --abbrev-commit --oneline --graph --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d'"
   git config --global alias.repo-bd "log --abbrev-commit --oneline --graph --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d' main..HEAD"
   git config --global alias.stat 'status --short --branch --untracked-files=all'
   ```

   You will learn why these aliases are useful as you progress through this walk-through.

## Git Core Concepts and Definitions

{% include todo.html content="
Other stuff to mention:
- Branch naming requirements and conventions
- Tag naming requirements and conventions
- Keep each project and learning exercise in a separate git repository
- The conceptionalisation of a commit as a version vs. as a change
- Stashes
" %}

### Repositories, Commits, and the Initial Commit

Git allows initially saving a copy of a subset[1] of the files (called the **tracked files**) within[2] a directory (called the **git root directory**) as a version (called a **commit**) whenever the user requests it. After creating this **initial commit**, git allows saving the **changes** made to the set of tracked files since the last commit (which may include the creation and deletion of files) as a new commit whenever the user requests it (ie. when the user *commits* to keeping the changes). Creating commits builds up a **history** of the set of tracked files as a whole[3]. Git stores this history in a sub-directory of the git root directory called `.git`.

Git allows copying the history from any git root directory to another location, such as another computer or a server. Each copy of the history, including the original copy[4], is called a **clone**. The history of each clone can be modified independently after cloning. The combined history of all clones that share an initial commit is called a **git repository**[5].

It's important to note that this definition of 'git repository' makes it an abstract concept - there is no single location of 'a repository'; a repository is **distributed** across all of its clones.

{% include info.html content="
**Key Point**: Git doesn't store complete versions of your files (except in the initial commit); it stores the **changes** between versions.
" %}

**Key Concepts**:

- Git root directory
- Tracked files
- Commits
- Initial commit
- Changes
- History
- Clones
- Repositories

**Visualisation of concepts so far**:

![Git concepts: repositories, commits, and the initial comit - overview]({{site.url}}/assets/images/version-control/git-concepts-repo-commit-and-initial-commit.drawio.png)

### Changes and The Working Tree

Most clones[6] of a repository have a location (called the **working tree**) where the tracked files from one of the commits in the repository are placed (called being **checked out**, like a library book) so that they can then be edited (ie. *worked* on, hence it's called the *working* tree). By default, this is the same location as the git root directory of the clone.

After making any desired changes, the changes must be added to the **index** before they can be committed. The index stores what the next commit would be if the user committed right now - it acts like a 'staging area' before the changes it contains are committed. Once the index contains a single stable and coherent set of changes, the user can commit those changes.

Any changes to tracked files made to the working tree that haven't been added to the index are called **unstaged changes**. Any changes added to the index are called **staged changes**.
The combination of all staged *and* unstaged changes are called **uncommitted changes**.

**Key Concepts**:

- The working tree
- The index
- The checked-out commit
- Names for specific sets of changes:
  - Unstaged changes
  - Staged changes
  - Uncommitted changes

### More on Tracked Files

With the above definitions in hand, we can refine our definition of *tracked file*.

A file is tracked in a clone if it exists in the currently checked-out commit (regardless of whether that commit directly contains any changes to it), or there are any changes to it in the index (including creation or deletion).

Therefore:

- Adding "the creation of a file" (as a change) to the index (even before comitting) makes that file tracked because there is a change to it (creation) in the index.

- Adding "the removal of a file" (as a change) to the index *and committing it* will make that file no longer tracked because it will no longer exist in the checked-out commit (which is the new commit) and there are no changes to it in the index.

Directories are not tracked.

**Key Concepts**:

- Tracked files (more details)

**Visualisation of concepts so far**:

![Git concepts: the working tree, tracked files, and changes]({{site.url}}/assets/images/version-control/git-concepts-the-working-tree-tracked-files-and-changes.drawio.png)

### References and Checkout - Branches, Tags, and `HEAD`

When a git repository (ie. an initial commit) is created, git automatically creates a note (called a **reference**, or **ref**) that refers to the initial commit. After this, whenever the user commits changes, this reference is updated to refer to the new commit. This kind of reference - one that updates to refer to the new commit whenever you commit - is called a **branch**. The commit that a branch refers to is called the **tip** of the branch. The branch that git automatically creates when the initial commit is created is called the **default branch**[7].

Once the default branch is created, git allows making more branches. Branches allow working on and committing different sets of changes (called **divergent** histories) to the same files separately, as if making those different changes to separate copies of the files. However, unlike editing multiple copies, git keeps track of divergent changes in a way that provides much greater flexibility to combine (which git calls **merge**) different sets of changes in various ways.

Only one branch can be checked out into the[8] working tree at any one time, but the user can switch between branches at any time[9]. Git has a special reference called **`HEAD`** that normally refers to the *branch* that is currently checked out (rather than the commit that the branch refers to). This means that when you commit and the branch is updated to refer to the new commit, `HEAD` will ultimately refer to the new commit as well. Git automatically sets `HEAD` to the default branch when the initial commit is created.

It is also possible to check out any commit, rather than a branch. This will put you into **detached `HEAD`** mode, which operates the same as **attached `HEAD`** mode (ie. the normal mode), except that since there is no branch checked out, then any commits you make will only be refered to by `HEAD` and not by any branch. As such, if you change `HEAD` by checking out another commit or a branch, then all of the additional commits you have created since detaching `HEAD` will become **orphaned**, and so will become inaccessible using the 'normal' git commands and will be marked for deletion[10]. If you want to keep the work you have done after checking out a commit directly (and so detaching `HEAD`), then create a branch that refers to the commit you currently have checked out before checking out another commit or a branch.

Finally, git allows you to create static references called **tags** that do not change when you commit. If you check out a tag, git will detach your `HEAD` and update it to refer to the commit that the tag refers to, rather than to the tag itself. Tags tend to be used to mark specific, historical versions of the files, such as previous 'releases' of a piece of software.

**Key Concepts**:

- Refs, and the different kinds of refs ...
- Branches
- HEAD
- Tags

**Visualisation of concepts so far**:

![Git concepts: references and detached HEAD - overview]({{site.url}}/assets/images/version-control/git-concepts-references-and-checkout.drawio.png)

### Footnotes

- [1] Possibly all files, or possibly no files.
- [2] Files within any sub-directory of the git root directory, or any sub-directory of those, etc. can also be tracked by git.
- [3] Rather than for each file separately.
- [4] A git root directory is always the root directory of a clone, except before the git root directory has an initial commit. A git root directory without an initial commit *has no history* and therefore doesn't contain a repository, doesn't contain a clone, and isn't clonable.
- [5] Some people and organisations define 'git repository' as the same as the above definition of 'clone'. However, a distinction has been made in this walk-through partly to reflect how the term is often used in practice, and partly so that we can more easily discuss the distributed nature of git.
- [6] Non-bare clones. Bare clones only contain the history, with no working tree. Bare repositories are intended to be used for integrating a team's changes, like they are on version control hubs, rather than as a clone for making changes to the tracked files in the repository.
- [7] The name of the default branch was configured in the previous section, but it is called `main` throughout this walk-through.
- [8] Git supports having multiple working trees for a single clone, but this feature is rarely used because it is rarely useful - you can't physically work on multiple things at once (and shouldn't try to because multi-tasking makes you less productive), and keeping track of which version you're working on can be difficult and lead to confusion, so switching branches is usually the *more* efficient way of working.
- [9] If you switch branches while you have uncommitted changes, then git will try to apply those changes 'on top of' the content of the files from the commit at the tip of the newly checked-out branch. If git is unable to do this automatically, it will put the files for which it is unable to do it into an 'unmerged' state due to 'merge conflicts'. Merge conflicts, including other circumstances that they can happen in and how to resolve them, is discussed in much more detail later in this walk-through.

## Full Walk-Through

### Initialising a Git Root Directory

To make a directory into a git root directory (by creating the `.git` directory inside of it), set the current directory to the desired directory, then run the following command:

```sh
git init
```

{% include tip.html content="
The `.git` directory is a hidden file (because its name starts with a `.`), so you'll have to show hidden files in your file manager to see it. It is generally recommended to show hidden files and show file extensions while doing software engineering. If working on Windows, both of these settings are in the View menu of Windows Explorer (the default file manager on Windows systems).
" %}

{% include warning.html content="
Once created, **DO NOT directly modify files** inside the `.git` directory. Doing so could corrupt the versioning metadata held by that clone of the repository, making git no longer able to manage that clone.

Also note that deleting a `.git` directory will delete all of the versions and all other versioning metadata that git has stored in that clone of the git repository. Some of this data may be available from other clones of the repository (if there are any), but some of it may not be.
" %}

### Starting a Repository

To start a repository on a newly-initialised git root directory, create an initial commit. It is generally recommended to make the initial commit empty so that all content of the repo is easily rebasable. Git will refuse to create an empty commit by default, so add `--allow-empty` to `git commit` to force it:

```sh
git commit --allow-empty
```

### TODO

{% include todo.html content="**TODO**" %}

# Appendices

## Appendix 1: Common Git Configurations

### Viewer and Editor

To use `nano` as editor, run:
```sh
git config --global core.editor nano
```

To instead use VS Code as editor, difftool, and mergetool:
```sh
git config --global core.editor 'code --wait'
git config --global diff.tool 'default-difftool'
git config --global difftool.default-difftool.cmd 'code --wait --diff $LOCAL $REMOTE'
git config --global merge.tool 'code'
git config --global mergetool.code.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
```
Source: https://code.visualstudio.com/docs/sourcecontrol/overview#_vs-code-as-git-editor

Do a web search for "git core.editor <your preferred editor>" for information on how to configure other editors.

### Command Aliases

**Notes**:

- In my suggested initial set of aliases, the `l` in `repo-l` stands for 'linear', meaning it only outputs the commits reachable from the currently checked-out commit, rather than reachable from any reference in the repository. The `b` in `repo-b` stands for 'branch', meaning it outputs the same as `repo-l`, except it excludes all commits that are *also* reachable from the `main` branch.

- If any options/arguments are added to the end of a command that runs a git alias, then those options/arguments are added to the end of the command that the alias 'stands for' before running the full command, eg. `git repo-l branch-a..branch-b` becomes `git log --abbrev-commit --format=oneline --graph branch-a..branch-b` if the `repo-l` alias is defined as above.

### My Full Configuration

```sh
git config --global user.name 'William Taylor'
git config --global user.email 'williamtaylordev@gmail.com'
git config --global init.defaultBranch main
git config --global core.editor nano

git config --global alias.repo 'log --abbrev-commit --format=oneline --graph --all'
git config --global alias.repo-l 'log --abbrev-commit --format=oneline --graph --all'
git config --global alias.repo-b 'log --abbrev-commit --oneline --graph main..HEAD'
git config --global alias.repo-d "log --abbrev-commit --oneline --graph --all --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d'"
git config --global alias.repo-ld "log --abbrev-commit --oneline --graph --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d'"
git config --global alias.repo-bd "log --abbrev-commit --oneline --graph --date=short --format='%C(yellow)%<|(15)%h %C(cyan)%<|(30)%ad %C(yellow)%<|(50)%an %C(reset)%s%C(auto)%d' main..HEAD"
git config --global alias.stat 'status --short --branch --untracked-files=all'
```
