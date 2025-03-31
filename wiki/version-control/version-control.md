---
layout: main
title: Version Control

decks:
   version_control:
      name: Version Control
      slides:
      - vc-installation
      - vc-configuration
      - vc-repos-and-commits
      - vc-figure-repos-and-commits
      - vc-changes-and-working-tree
      - vc-tracked-files-details
      - vc-figure-worktree-tracking-and-changes
      - vc-branches-and-head
      - vc-detached-head-and-tags
      - vc-figure-refs-and-checkout
      - vc-views-of-commits
      - vc-checkout-vs-switch
---

{% include slider.html deck=page.decks.version_control %}




## Git Conventions

{% include todo.html content="
Other stuff to mention:
- Branch naming requirements and conventions
- Tag naming requirements and conventions
- Keep each project and learning exercise in a separate git repository
- Stashes
" %}

## Full Walk-Through

### Initialising a Git Root Directory

To make a directory into a git root directory (by creating the `.git` directory inside of it), set the current directory to the desired directory, then run the following command:

```sh
git init
```

{% include tip.html content="
The `.git` directory is a hidden file (because its name starts with a `.`), so you'll have to show hidden files in your file manager to see it. It is generally recommended to show hidden files and show file extensions while doing software engineering. If working on Windows, both of these settings are in the View menu of File Explorer (the default file manager on Windows systems).
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

### Adding Changes and Committing

{% include todo.html content="**TODO**" %}

### TODO

{% include todo.html content="**TODO**" %}










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

## Footnotes

[^1]: Possibly all files, or possibly no files.
[^2]: Files within any sub-directory of the git root directory, or any sub-directory of those, etc. can also be tracked by git.
[^3]: Rather than for each file separately.
[^4]: A git root directory is always the root directory of a clone, except before the git root directory has an initial commit. A git root directory without an initial commit *has no history* and therefore doesn't contain a repository, doesn't contain a clone, and isn't clonable.
[^5]: Some people and organisations define 'git repository' as the same as the above definition of 'clone'. However, a distinction has been made in this walk-through partly to reflect how the term is often used in practice, and partly so that we can more easily discuss the distributed nature of git.
[^6]: Non-bare clones. Bare clones only contain the history, with no working tree. Bare repositories are intended to be used for integrating a team's changes, like they are on version control hubs, rather than as a clone for making changes to the tracked files in the repository.
[^7]: The name of the default branch was configured in the previous section, but it is called `main` throughout this walk-through.
[^8]: Git supports having multiple working trees for a single clone, but this feature is rarely used because it is rarely useful - you can't physically work on multiple things at once (and shouldn't try to because multi-tasking makes you less productive), and keeping track of which version you're working on can be difficult and lead to confusion, so switching branches is usually the *more* efficient way of working.
[^9]: See [Checkout vs. Switch](#checkout-vs-switch) for caveats.
[^10]: You also have the option to perform a merge on checkout (`git checkout -m <other-branch>`), or force the checkout and discard your changes (`git checkout -f <other-branch>`), but these are rarely used - if you have merge conflicts, it is usually better to commit and perform a manual rebase, and discarding your changes is rarely what you want to do in the case of merge conflicts.
[^11]: Or you can do a 'soft' reset, which makes them staged.
