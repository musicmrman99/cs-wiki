---
ref: vc-repos-and-commits
type: info
---

### Repositories, Commits, and the Initial Commit

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
**Key Point**: It is often useful to view commits as the **changes** between versions of the set of tracked files, rather than as complete versions of those files (except the initial commit).

We go into more detail about this later, in the section [Views of Commits](#views-of-commits), but that section will make more sense if you understand more of git's core concepts first.
" %}

## Footnotes

[^1]: All files, some files, or no files.
[^2]: Files within any sub-directory of the git root directory, or any sub-directory of those, etc. can also be tracked by git.
[^3]: Rather than for each file separately.
[^4]: A git root directory is always the root directory of a clone, except before the git root directory has an initial commit. A git root directory without an initial commit *has no history* and therefore doesn't contain a repository, doesn't contain a clone, and isn't clonable.
[^5]: Some people and organisations define 'git repository' as the same as the above definition of 'clone'. However, a distinction has been made in this walk-through partly to reflect how the term is often used in practice, and partly so that we can more easily discuss the distributed nature of git.
