# Git More

Assorted helpers for working with git.

## Install

Add the path to this installation directory to you `.bashrc` (or `.bash_profile` for OS X).

**Example**
```
# Load git commands and aliases from git-more  <https://github.com/Erik-Codeblind/git-more>
export PATH="$PATH:$HOME/Development/git-more"
export XDG_CONFIG_HOME="$HOME/Development/git-more"
```

# git/conf

This includes a custom git config file with numerous aliases. Have a look therein for more information. Your global `.gitconfig` can be used to override and augment any rules defined here.

## git-pull-request-checkout (aliases: copr, prco)

Fetches the HEAD of a pull request by the PR ID and checks it out as a new branch. If the optional second argument is passed, it will be used to name the new branch, otherwise the branch will be named with the PR ID

***Examples***

Naming the branch.
```
git copr 976 FETCH_HEAD
[...snip...]
 * [new ref]         refs/pull/976/head -> my_branch
Switched to branch 'my_branch'
```

Defaulting to pull request ID for branch name.
```
git copr 977
[...snip...]
 * [new ref]         refs/pull/977/head -> 977
Switched to branch '977'
```

No pull request found throws expected error.
```
git copr 978
fatal: Couldn't find remote ref pull/1000/head
```

## git-bulk-delete (del)

Loops over branches in a repo and provides the user with an opportunity to delete the current one. By default, "master" and "develop" branches will be ignored, so you can't accidentally deleting them.

Enter "y" or "yes" to run `git branch -d` on the listed branch. Entering "q" or "quit" will exit the program. Empty return skips to the next current item.

## git-find-branch (fbr)

Runs a grep expression against the branches in your repo. If a solitary match is found, it will check out that branch immediately. When multiple matches are located, they will be listed and user my select which one to checkout. An empty returns quits without changing from the current branch.
  
**Examples**

Our working directory has three branches.
```
$ git branch
  exampleA
* master
  example1
```

Search for branches with "example" in their name and checkout item 1, *example1*.
```
git find-branch example
Found the following...
0: exampleA
1: example1
Which branch should I checkout? 1
Switched to branch 'example1'
```

Search for branch "master". There is only one match, so it is immediately checked out.
```
$ git find-branch master
M       README.md
Switched to branch 'master'
```


## git-branchify (cob)

This command allows you to create new branches and automatically format the branch name to lower case with dashes. It is
useful for managing long branch names, especially when cutting and pasting. The new branch is created of the current branch
using `git checkout -b`.

**Example**
```
$ git branchify Branchify Makes It Easy To Cut-and-Paste Branch Names
Switched to a new branch 'branchify-makes-it-easy-to-cut-and-paste-branch-names'
```

### Common prefixes (bug, feature, hotfix, spike)

Aliases exist to create common branch fixes.

```
$ git bug Fixing This Bug
Switched to a new branch 'bug/fixing-this-bug'
```

```
$ git feature My New Feature
Switched to a new branch 'feature/my-new-feature'
```

```
$ git hotfix Oh NO A Hotfix
Switched to a new branch 'hotfix/oh-no-a-hotfix'
```

```
$ git spike Giving this a try
Switched to a new branch 'spike/giving-this-a-try'
```