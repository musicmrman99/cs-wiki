---
ref: vc-views-of-commits
type: info
---

### Views of Commits

{% include plain-aside.html content="
**Key Concepts**:

- Snapshots vs. Changes
" %}

There are two ways of thinking about a commit - as a **change**, and as a **snapshot** (ie. the set of all files that you would get if you checked out the commit). Git views commits in these different ways in different contexts (such as in different `git` commands).

When you want to *use* the files that a commit represents (such as to run them, deploy them, share them, etc), you will view that commit like a snapshot. Tags are designed to be viewed like this - they are created to be checked out in future and used without making further changes.

When you want to *change* the files that a commit represents, you will view that commit like a snapshot (putting it in the role of a **base commit**), and view the set of commits based on it like changes. Branches are designed to be viewed like this - with the most recent commit that is reachable from both a given branch and the default branch being seen as the base commit, and the commits on that branch being seen as changes that make up the overall change of the branch.
