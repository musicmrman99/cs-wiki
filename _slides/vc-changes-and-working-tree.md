---
ref: vc-changes-and-working-tree
---

## Changes and The Working Tree

{% include plain-aside.html content="
**Key Concepts**:

- The working tree
- The index
- The checked-out commit
- Names for specific sets of changes:
  - Unstaged changes
  - Staged changes
  - Uncommitted changes
" %}

Most clones[^1] of a repository have a location (called the **working tree**) where the tracked files from one of the commits in the repository are placed (called being **checked out**, like a library book) so that they can then be edited (ie. *worked* on, hence it's called the *working* tree). By default, this is the same location as the git root directory of the clone.

After making any desired changes, the changes must be added to the **index** before they can be committed. The index stores what the next commit would be if the user committed right now - it acts like a 'staging area' before the changes it contains are committed. Once the index contains a single stable and coherent set of changes, the user can commit those changes.

Any changes to tracked files made to the working tree that haven't been added to the index are called **unstaged changes**. Any changes added to the index are called **staged changes**.
The combination of all staged *and* unstaged changes are called **uncommitted changes**.

## Footnotes

[^1]: Non-bare clones. Bare clones only contain the history, with no working tree. Bare repositories are intended to be used for integrating a team's changes, like they are on version control hubs, rather than as a clone for making changes to the tracked files in the repository.
