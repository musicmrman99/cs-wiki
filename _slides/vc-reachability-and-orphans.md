---
ref: vc-reachability-and-orphans
type: info
---

### Reachability and Orphaned Commits

{% include plain-aside.html content="
**Key Concepts**:

- Reachability
- Orphaned commits
- Garbage collection
" %}

With the above definitions in hand, we can refine our definition of *orphaned commit*.

Orphaned commits are those that are **unreachable** from any reference (`HEAD`, branch, tag, stash, etc). One way to find which commits are **reachable** is to pick a reference in your clone, then run through the following steps[^1] while making a list of of every commit you point at:

1. Point at the commit that your chosen revision resolves to.
2. If the commit you are pointing at is:
   1. Already on your list of commits, then skip to step 4.
   2. Not based on any other commit, then skip to step 4.
   3. Based on one other commit, then point at that commit.
   4. Based on two other commits, then point at one of them and take a note of the other.
3. Return to step 2.
4. If you have taken a note of any commit in step 2(i) that is not scribbled out, then point at any of them, scribble out the note you selected, and return to step 2.

Then do this for each reference in your clone, re-using the list of commits you come out with for all references. At this point, any commit you have on your list is reachable from at least one reference. Any commit that is not on your list is unreachable from any reference, ie. orphaned. Git considers all orphaned commits to be 'garbage' and will eventually delete them automatically. You can also tell git to run a **garbage collection**, though this rarely needs to be done manually.

### Terminology: "On A Branch"

In common usage, the phrase "**on a branch**" means different things in different contexts:

- If someone is talking about *you* (the user) being 'on' a branch, they mean which branch you have checked out.
- If someone is talking about a *commit* being 'on' a branch, they usually mean that the commit is reachable from that branch, but is unreachable from the default branch.
- Occasionally, especially if they are talking about older commits, they may just mean that the commit is reachable from that branch, even if it is also reachable from the default branch.

When in doubt, clarify what was meant. This walk-through will only use the second meaning, except when talking about a commit being 'on' the default branch, in which case it uses the third meaning.

## Footnotes

[^1]: If you're already familiar with algorithms and data structures in programming, you may notice that this is a `goto`-based depth-first traversal of the directed acyclic graph of all commits, starting from a given reference.
