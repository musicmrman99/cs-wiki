---
layout: main
title: Version Control

decks:
   vc_intro:
      title: "Version Control: Git Introduction"
      slides:
      - vc-installation
      - vc-configuration

   vc_concepts:
      title: "Version Control: Git Core Concepts"
      slides:
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

{% include slider.html deck=page.decks.vc_intro %}
{% include slider.html deck=page.decks.vc_concepts %}

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
Source: [https://code.visualstudio.com/docs/sourcecontrol/overview#_vs-code-as-git-editor](https://code.visualstudio.com/docs/sourcecontrol/overview#_vs-code-as-git-editor)

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
