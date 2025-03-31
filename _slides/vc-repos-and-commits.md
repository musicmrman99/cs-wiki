---
ref: vc-repos-and-commits
---

## Repositories, Commits, and the Initial Commit

{% include plain-aside.html content="
**Key Concepts**:

- Git root directory
- Tracked files
- Commits
- Initial commit
- Changes
- History
- Clones
- Repositories
" %}

Git allows initially saving a copy of a subset[^1] of the files (called the **tracked files**) within[^2] a directory (called the **git root directory**) as a version (called a **commit**) whenever the user requests it. After creating this **initial commit**, git allows saving the **changes** made to the set of tracked files since the last commit (which may include the creation and deletion of files) as a new commit whenever the user requests it (ie. when the user *commits* to keeping the changes). Creating commits builds up a **history** of the set of tracked files as a whole[^3]. Git stores this history in a sub-directory of the git root directory called `.git`.

Git allows copying the history from any git root directory to another location, such as another computer or a server. Each copy of the history, including the original copy[^4], is called a **clone**. The history of each clone can be modified independently after cloning. The combined history of all clones that share an initial commit is called a **git repository**[^5].

It's important to note that this definition of 'git repository' makes it an abstract concept - there is no single location of 'a repository'; a repository is **distributed** across all of its clones.

{% include info.html content="
**Key Point**: Git doesn't store complete versions of your files (except in the initial commit); it stores the **changes** between versions.
" %}

{% include todo.html content="
The above is technically incorrect, but is close to the implementation. Regardless, it may be worth re-wording to closer match the section on [Views of Commits](#views-of-commits).
" %}
