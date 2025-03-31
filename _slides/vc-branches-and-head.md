---
ref: vc-branches-and-head
---

## Branches and `HEAD`

{% include plain-aside.html content="
**Key Concepts**:

- Refs (in general)
- Branches
- HEAD
" %}

When a git repository (ie. an initial commit) is created, git automatically creates a note (called a **reference**, or **ref**) that refers to the initial commit. After this, whenever the user commits changes, this reference is updated to refer to the new commit. This kind of reference - one that updates to refer to the new commit whenever you commit - is called a **branch**. The commit that a branch refers to is called the **tip** of the branch. The branch that git automatically creates when the initial commit is created is called the **default branch**[^7].

Once the default branch is created, git allows making more branches. Branches allow working on and committing different sets of changes (called **divergent** histories) to the same files separately, as if making those different changes to separate copies of the files. However, unlike editing multiple copies, git keeps track of divergent changes in a way that provides much greater flexibility for combining (called **merging**) different sets of changes in various ways.

Only one branch can be checked out into the working tree[^8] at any one time, but the user can switch between branches[^9]. Git has a special reference called **`HEAD`** that normally refers to the *branch* that is currently checked out (rather than the commit that the branch refers to). This means that when you commit and the branch is updated to refer to the new commit, `HEAD` will implicitly refer to the new commit as well. Git automatically sets `HEAD` to the default branch when the initial commit is created.
