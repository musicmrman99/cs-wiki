---
ref: vc-detached-head-and-tags
---

### Detached `HEAD` and Tags

{% include plain-aside.html content="
**Key Concepts**:

- Detatched HEAD
- Tags
" %}

It is also possible to checkout any commit, rather than a branch. This will put you into **detached `HEAD`** mode, which operates the same as **attached `HEAD`** mode (ie. the normal mode), except since there is no branch checked out, any commits you make will only be refered to by `HEAD` and not by any branch. As such, if you change `HEAD` by checking out another commit or a branch, then all of the additional commits you have created since detaching `HEAD` will become **orphaned**, and so will become inaccessible using the 'normal' git commands and will be marked for deletion. If you want to keep the work you have done after checking out a commit directly (and so detaching `HEAD`), then create a branch that refers to the commit you currently have checked out before checking out another commit or a branch.

Finally, git allows you to create static references called **tags** that do not change when you commit. If you checkout a tag, git will detach your `HEAD` and update it to refer to the commit that the tag refers to, rather than to the tag itself. Tags tend to be used to mark specific, historical versions of the files, such as previous 'releases' of a piece of software.
