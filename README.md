




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


#### local workflow

![alt text](https://cdn-images-1.medium.com/max/800/1*diRLm1S5hkVoh5qeArND0Q.png)

`git init`

`git status`

`git lg`

`git add`

`git commit `


**Moving in history**

`git checkout <SHA>`


**Branches**

git branch -av

`git checkout -b newBranchName`



**Merge**


**Submodules** 


**Undo things**




#### adding remote for myself




#### collaboration 





<br> 
---
### Github

* make github account 

* setup ssh following [these instructions](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh) so you can directly push to your repos without password






<br> 
--- 
### GitKraken




