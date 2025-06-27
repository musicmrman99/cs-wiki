---
ref: vc-checkout-vs-switch
type: info
---

### Checkout vs. Switch

{% include plain-aside.html content="
**Key Concepts**:

- Rebase on checkout
- Reset
- The relationship between `HEAD` and the working tree
" %}

So far we've seen making changes on top of a checked-out commit, and checking out a different branch before making any changes, but what about checking out a different branch after making changes? If you checkout a branch while you have uncommitted changes, then git will try to apply those changes to the content of the files from the commit at the tip of the newly checked-out branch (or from the newly checked-out commit, if detaching `HEAD`). This is called **rebasing** your changes - where a set of changes originally made to one base commit is applied to another base commit. If git is unable to do this rebase automatically, it will abort the checkout[^1]. Rebase-on-checkout is primarily useful when you have made some changes, but you had a different branch checked out at the time you made them than the branch you wanted to commit them to.

{% include todo.html content="
THE FOLLOWING IS NOT TRUE.

`git reset` does not perform a switch. If in attached `HEAD` mode, it will change the commit your current branch refers to without changing which branch your `HEAD` refers to.
" %}

It is also possible to switch to a different branch (or commit, if detaching `HEAD`) without changing the working tree *at all*. This is called **resetting**, and effectively marks all of the changes between the previous working tree and the new `HEAD` commit (viewed as a snapshot) as unstaged[^2]. Resetting cannot cause merge conflicts. Resetting to `HEAD` simply unstages all of your staged changes. Resetting is primarily useful when you accidentally added (or committed after adding) fewer or more changes than you thought you had made, or when you want to split a commit (viewed as a change) into multiple commits.

{% include info.html content="
**Key Point**: Changing `HEAD` (switch) is separate from changing the working tree (checkout).

Several commands both switch and checkout in one go, but these operations should be thought about separately. Rebase-on-checkout moves your changes onto a new `HEAD` (keeping your *changes* the same, but changing your snapshot), while reset just moves `HEAD` (keeping your *snapshot* the same, but combining your changes).
" %}

## Footnotes

[^1]: You also have the option to perform a merge on checkout (`git checkout -m <other-branch>`), or force the checkout and discard your changes (`git checkout -f <other-branch>`), but these are rarely used. If you have merge conflicts, it is usually better to commit and perform a manual rebase. You would rarely want to discard your changes in the case of merge conflicts.
[^2]: Or you can do a 'soft' reset, which makes them staged.
