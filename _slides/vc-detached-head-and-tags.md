---
ref: vc-detached-head-and-tags
type: info
---

### Detached `HEAD` and Tags

{% include plain-aside.html content="
**Key Concepts**:

- Commit IDs
- Detatched HEAD
- Tags
- Revisions
" %}

Every commit is uniquely identified by a **commit ID**. Commit IDs are strings of 40 characters containing letters and numbers, though many git commands only show the first 7 or 8 characters for brevity. Two commits with the same changes will still have different IDs[^1].

It is also possible to checkout a commit directly by using its commit ID, rather than a branch. This will put you into **detached `HEAD`** mode. This operates similarly to **attached `HEAD`** mode, treating `HEAD` like a branch and updating it to refer to the new commit whenever you commit, except that if you change `HEAD` by checking out another commit or a branch, then all of the additional commits you have created since detaching `HEAD` will become **orphaned**. Orphaned commits are hidden/ignored by default in most git commands, and will eventually be deleted automatically. If you want to keep the work you have done after checking out a commit directly (and so detaching `HEAD`) and commiting, then create a branch that refers to your latest commit before checking out another commit or branch.

Git also allows you to create static references called **tags** that do not change when you commit after checking them out. If you checkout a tag, git will detach your `HEAD` and set it to refer to the commit that the tag refers to, rather than to the tag itself. Tags tend to be used to mark specific, historical versions of the files, such as previous 'releases' of a piece of software.

Many git commands operate on commits rather than (or as well as) references. When these commands are given references, they first find the commits those references refer to, possibly via other references (such as needing to find the branch that an attached `HEAD` refers to, before finding the commit that branch refers to). These commands also support being given commit IDs directly. Git commands ask for **revisions** in these cases, meaning "a reference or a commit ID".

## Footnotes

[^1]: This becomes important later when we discuss rebasing commits.
