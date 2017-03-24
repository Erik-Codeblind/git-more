# Git More

Assorted helpers for working with git.

## Install

Add the path to this installation directory to you `.bashrc` (or `.bash_profile` for OS X).

**Example**
```
export PATH="$PATH:$HOME/Development/git-more" # More git commands
```

## git-bulk-delete

Loops over branches in a repo and provides the user with an opportunity to delete the current one. Type "y" or "yes" to run `git branch -d` on the listed branch. Defaults to "no", which moves the pointer to the next item without deleting anything. By default, "master" and "develop" branches will be ignored, so you can't accidentally deleting them.

``` 
git bulk-delete
   Delete branch test-branch [no]? yes
   Deleted branch test-branch (was 7226003).
```



## git-find

Runs a grep expression against the branches in your repo. If only a single match is found, it will check out that branch immediately. When multiple matches are found, they will be listed such that you may select which one to checkout.
  
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
git find test
Found the following...
0: exampleA
1: example1
Which branch should I checkout? [quit] 1
Switched to branch 'example1'
```

Search for branch "master". There is only one, so it is immediately checked out.
```
$ git find master
M       README.md
Switched to branch 'master'
```


## git-branchify

This command allows you to create new branches and automatically format the branch name to lower case with dashes.

`git branchify My Brand New Branch` translates to `git checkout -b my-brand-new-branch` .

**Example**
```
$ git branchify Branchify Makes It Easy To Cut-and-Paste Branch Names
Switched to a new branch 'branchify-makes-it-easy-to-cut-and-paste-branch-names'
```

### Branchify Subcommands

#### git-bug
```
$ git bug Fixing This Bug
Switched to a new branch 'bug/fixing-this-bug'
```

#### git-feature
```
$ git feature My New Feature
Switched to a new branch 'feature/my-new-feature'
```

#### git-hotfix
```
$ git hotfix Oh NO A Hotfix
Switched to a new branch 'hotfix/oh-no-a-hotfix'
```

#### git-spike
```
$ git spike Giving this a try
Switched to a new branch 'spike/giving-this-a-try'
```