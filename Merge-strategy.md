Our general Git workflow is inspired by [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow).

We have two historical (long-lived) branches `master` and `develop`. The top revision of the `master` branch always represents the latest released version whereas `develop` points to the latest development version. Both branches must always be in a compilable and usable state and all tests must pass.

In addition to these two branches, there are several short-lived branches with different prefixes:

- **`feature/<issue#-description>`**: new features or non-critical fixes<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `develop` 
- **`release/<x.y.z>`**: release preparation branch for version *&lt;x.y.z&gt;*, marks beginning of feature freeze<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `develop`, `master`
- **`hotfix/<issue#-description>`**: maintenance branch for bugfixes in released versions<br>
   *Branch from:* `release/<x.y.z>`<br>
   *Merge back into:* `release/<x.y.z>`, `develop`
- **`meta/<description>`**: patches that don't directly affect the application (documentation, build organization etc.)<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `develop`

Merging from a short-lived branch into a historical should be done using `git merge --no-ff` to preserve the origin of those commits. For instance, if a `feature/*` branch is merged into `develop` it should be done with a merge commit.

Merging from historical branches into short-lived branches cannot be done without a merge commit, so it is preferred to keep the short-lived branch rebased on top of the long-lived branch (i.e., rebase your `feature` onto the `develop` branch). If that is not possible because the branch is used by multiple contributors, a normal merge commit is acceptable.

Merging a `hotfix` into the `release` branch should be done using `git merge --ff-only` or `git rebase (--onto)` and then `git merge --ff-only` to avoid creating a merge commit. The same applies when merging between other short-lived branches. Avoid merge commits where possible. The exception is when the merged branch contains a significant number of commits and preserving the two branches in the history makes sense (*significant* is subjective).

Merging a `release` branch into `master` and `develop` should be done using `git merge --no-ff`.