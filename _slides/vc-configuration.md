---
ref: vc-configuration
type: info
---

### Configuring Git

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
