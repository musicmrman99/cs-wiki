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

When a git repository (ie. an initial commit) is created, git automatically creates a note (called a **reference**, or **ref**) that refers to the initial commit. After this, whenever the user commits changes, this reference is updated to refer to the new commit. This kind of reference - one that updates to refer to the new commit whenever you commit - is called a **branch**. The commit that a branch refers to is called the **tip** of the branch. The branch that git automatically creates when the initial commit is created is called the **default branch**[^1].

Once the default branch is created, git allows making more branches. Branches allow working on and committing different sets of changes (called **divergent** histories) to the same files separately, as if making those different changes to separate copies of the files. However, unlike editing multiple copies, git keeps track of divergent changes in a way that provides much greater flexibility for combining (called **merging**) different sets of changes in various ways.

Only one branch can be checked out into the working tree[^2] at any one time, but the user can switch between branches[^3]. Git has a special reference called **`HEAD`** that normally refers to the *branch* that is currently checked out (rather than the commit that the branch refers to). This means that when you commit and the branch is updated to refer to the new commit, `HEAD` will implicitly refer to the new commit as well. Git automatically sets `HEAD` to the default branch when the initial commit is created.

## Footnotes

[^1]: The name of the default branch was configured in the previous section, but it is called `main` throughout this walk-through.
[^2]: Git supports having multiple working trees for a single clone, but this feature is rarely used because it is rarely useful - you can't physically work on multiple things at once (and shouldn't try to because multi-tasking makes you less productive), and keeping track of which version you're working on can be difficult and lead to confusion, so switching branches is usually the *more* efficient way of working.
[^3]: See [Checkout vs. Switch](#checkout-vs-switch) for caveats.
