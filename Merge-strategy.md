Our general Git workflow is loosely inspired by [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow).

## Branch Names

We have two eternal (long-lived) branches `master` and `develop`. The top revision of the `master` branch always represents the latest released version whereas `develop` points to the latest development version. Both branches must always be in a compilable and usable state and all tests must pass.

In addition to these two branches, there are several short-lived topic branches with different prefixes:

- **`feature/<issue#-description>`**: new features or non-critical fixes<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `develop` 
- **`release/<x.y.z>`**: release preparation branch for version *&lt;x.y.z&gt;*, marks beginning of feature freeze<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `master`
- **`hotfix/<issue#-description>`**: maintenance branch for bugfixes in released versions<br>
   *Branch from:* `release/<x.y.z>`<br>
   *Merge back into:* `release/<x.y.z>`, `develop`
- **`meta/<description>`**: patches that don't directly affect the application (documentation, build organization etc.)<br>
   *Branch from:* `develop`<br>
   *Merge back into:* `develop`

## Merging Strategy and Requirements

Merging a topic branch into an eternal or release branch should always be done in a fast-forward manner. That means it needs to be [rebased](https://git-scm.com/docs/git-rebase) properly onto the latest revision of the target branch (usually `develop`) and merging is done without creating a merge commit (`git merge --ff`). Each commit on a merged branch needs to compile, pass all tests, and be in a usable state. Unless there is a very good reason for separating individual changes, this means that all changes of a branch should be merged into a single commit once a feature has been completed.

Merged commits need to be descriptive. For very small commits this means they need to have a good title. For larger commits, add an exhaustive description about what the patch does and why after the title. Reference issues liberally.

If your branch does not meet the above-mentioned commit requirements, maintainers will squash-merge and rewrite your commit at will.