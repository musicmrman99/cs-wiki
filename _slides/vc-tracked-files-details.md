---
ref: vc-tracked-files-details
---

### More on Tracked Files

{% include plain-aside.html content="
**Key Concepts**:

- Tracked files (more details)
" %}

With the above definitions in hand, we can refine our definition of *tracked file*.

A file is tracked in a clone if it exists in the currently checked-out commit (regardless of whether that commit directly contains any changes to it), or there are any changes to it in the index (including creation or deletion).

Therefore:

- Adding "the creation of a file" (as a change) to the index (even before comitting) makes that file tracked because there is a change to it (creation) in the index.

- Adding "the removal of a file" (as a change) to the index *and committing it* will make that file no longer tracked because it will no longer exist in the checked-out commit (which is the new commit) and there are no changes to it in the index.

Directories are not tracked.
