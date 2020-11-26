




### Command line basics

Brief intro in [Datalad handbook](http://handbook.datalad.org/en/latest/intro/howto.html). 

More elaborate intro in this [tutorial](https://htmlpreview.github.io/?https://github.com/berkeley-scf/tutorial-using-bash/blob/master/bash.html). 

* bash commands have arguments and options 

```
mkdir myDirName
mkdir -p mySubdirName/myDirName 

```

* tab completion

* in Finder copy file or folder path to clipboard using `Cmd-Opt-C`

**Crucial commands to know**: 

`pwd` shows current working directory

`cd` changes working directory

`ls -lah` lists files in current working directory

* setup as alias `ll`, open `~/. bash_profile` and paste the following: 

```
alias l='ls -lah'
```

`. ` current directory

`.. ` one directory above the current one

`~ ` shortcut to home folder 


`tree ` 

* must be installed first on macOS `brew install tree`


`mkdir` makes new directory 

`cp` copies files

`mv` moves and renames files

`rm` removes files (dangerous, no way to restore!)

`rm -rf` removes directories and their contents (very dangerous!)







<br> 

---

### GIT

* setup username and email (these willl be displayed next to your commits) 

```
git config --global user.name "<Your-Full-Name>"
git config --global user.email "<your-email-address>"
```

* install [atom](https://atom.io/) and set it as default text editor 

```
git config --global core.editor "atom --wait"
```

* setup alias `git lg` for nice log graphs: 

Paste the following code into `~/.gitconfig` file: 

```
[alias]
    lg = lg1
    lg1 = lg1-specific --all
    lg2 = lg2-specific --all
    lg3 = lg3-specific --all

    lg1-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)'
    lg2-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)'
    lg3-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset) %C(bold cyan)(committed: %cD)%C(reset) %C(auto)%d%C(reset)%n''          %C(white)%s%C(reset)%n''          %C(dim white)- %an <%ae> %C(reset) %C(dim white)(committer: %cn <%ce>)%C(reset)'

```

<br> 

**Install GitKraken**





#### local workflow

![alt text](https://cdn-images-1.medium.com/max/800/1*diRLm1S5hkVoh5qeArND0Q.png)

`git init`

`git status`

`git add`

`git commit `

`git lg`

<br>
**Diff**

`git diff <SHAnew>..<SHAold>` compares 2 commits from history

`git diff HEAD~1` compares current HEAD to previous state


<br>

**Moving in history**

`git checkout <SHA>` 

* detached HEAD

<br>

**Branches**

`git branch -av` lists all branches

`git checkout -b newBranchName` makes a new local branch

`git checkout branchName` switches to existing branch
 
<br>

**Merge**

from branch *to* which you want to merge, type 

```
git merge branchFromWhichToMerge
```

`-ff` fast forward option (automatic if possible) makes not merge commit 


* merge conflict



<br> 

---

### Github


* make github account 

* setup ssh following [these instructions](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh) so you can directly push to your repos without password



<br>

#### adding remote for myself

`git remote add remoteName url` adds a remote repo (e.g. GitHub)

`git remote -v` shows existing remotes

`git push remoteName branchName`



<br>

#### collaboration in one shared repo 

`git fetch remoteName` 

`git pull remoteName branchName`

<br>

#### collaboration using pull-requests

* fork a repo on GitHub
* clone my forked repo from GitHub
* make a local branch 
* work on changes
* push the branch to my GitHub
* open pull-request on GitHub

`git clone url` make a local copy 


<br>

**Submodules** 

`git add submodule url` adds a git repo as submodule 

* after cloning a big repo repo that contains submodules, you must get these submodules manually: 

`git submodule init` update local config file with data from .gitmodules

`git submodule update` fetch and checkout the mapped commit in each submodule

* get nested submodules recursively

```
git submodule foreach --recursive 'git submodule init'
git submodule foreach --recursive 'git submodule update'
```

* to pull updates in the submodule manually, you need to be in the folder and type 

```
git fetch
git merge origin/master
```

if we pull a new commit of the parent repo where changes in the submodules are indicated, this doesn't automatically update the subomdule commits 

what you need to do is:  

```
git submodule update --recursive
```

Sometimes, from the parent repo, git status will show that the submodule directory was changed and git diff on that directory will show either different commit SHAs or same SHAs but the `+` one with "*dirty*" appended

Submodule is "dirty" if we edit files in the submodule. 

Example: 

Imagine we have nested submodules in a git repo

```
parent
	CPP_BIDS
		bids-matlab
```


let's say we go to CPP_BIDS and checkout a different branch

but let's say this branch points to different bids-matlab commit 

but bids-matlab doesn't update automatically, so from CPP_BIDS, and hence it will look like we have working tree changes in bids-matlab 

and when calling git diff from parent, we will see something like
> 	-Subproject commit 57738dc8bdfcf3c1db13d18edfbb1d1a9cedfe4e
> 	+Subproject commit dfa4bc80f60e3ed555805890254ef6189b63dc04-dirty

We need to go to CPP_BIDS, call: 

```
git submodule update --recursive
git submodule foreach --recursive "git submodule update"
```
and then the "dirty" flag will diappear (note we may still need to commit the change in subdataset SHA in the parent  





<br>

**Rebase**

* no merge commmit, keeps history clean

<br>

**Workflows**






---

<br>

**Undo things**


* add staged content to the last commit (and change the commit message)

```git commit --amend```

* if there is a new untracked file or non-added changes you want to remove

```
git checkout -- filename
```

the `--` is to separate the commits (there are none in this case cause we want the HEAD on the current branch, which is default) and filenames that should be checked out


* remove last commit, but keep the modifications as non-added 

```
git reset --mixed SHA
```

* remove last commit and discard the changes altogether (!dangerous)

```
git reset --hard SHA
```

!!! hard reset can be undone using reflog, just see where the HEAD was before and find the SHA you need

```
git reflog
```

* revert a single file to previous state (at commit <SHA>) and get the file 
modification from that point onwards back to working directory (don't change 
history or anything)

```
git checkout <SHA> -- filename
```

* reset to a specific commit 

```
git reset --hard <SHA>
```


* to undo changes but don't change history 

```
git revert <SHA>
```

* to remove new untracked files (e.g. after trying code that produces output, we need to clean this "testing" output before using "datalad run" (see [here](https://www.codegrepper.com/code-examples/shell/git+remove+Untracked+files))

dry run (see what would be removed)
```
git clean -n 
```

remove files (-f), directories (-d), ignored files (-X), ignored and 
nonignored files (-x)

```
git clean -fx
```

git clean and reset can be both used equivalently to clean working tree

only git reset can reset things in the staging index 





