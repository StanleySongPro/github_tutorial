# github_tutorial

**version 1.0.0**

---

## 1.	Command lines on github

* git status:                   check the status of local machine and remote repository
* git config:
* git help:
* git diff:                     show the changes made


* git add <filename>:           add new file or file with changes to github
* git add -A:                   add all to github
* git add .:                    add all to github
 

* git commit -m 'messages':     new file or changes committed but still on local machine
* git commit -a -m 'messages':  commit all the changes
* git log:                      get the history of all the commits


* git pull origin master:       syc everything in github.com to local machine
* git push origin master:       syc everything in local machine to github.com


* git clone github_url:         download files from the github
* git remote -v:                viewing info about the remote repository
* git branch -a:                viewing info about the branch
* git remote add origin <url_of_repo> (if you don't have the origin)


* git init:                     initialize the local repo
* rm -rf <.git>:                to remove the folder from git repository


* touch .gitignore
* git reset <filename>:         remove file in the staging area
* git reset:                    remove everything in the staging area

---

## 2.	[Github by tasks](https://www.youtube.com/watch?v=h1e8oC7g0Ps&index=11&list=PL5-da3qGB5IBLMp7LtN8Nc3Efd4hJq0kD):

### [Git quick reference for beginners](https://www.dataschool.io/git-quick-reference-for-beginners/)

### Copying a repo to your local computer
* **git clone <url_of_repo_othres>**
* **git remote -v**: show the references connected to your repo
* **git branch -r**: check the branches as well
* If origin is in the original repo that you wanna copy, add the orginal repo as upstream, delete origins and add your own repo, as below:
    #### Change "origin" of your GIT repository
    * git remote rm origin
    * git remote add origin <url_of_repo_own>
    * git config master.remote origin
    * git config master.merge refs/heads/master
* **git pull origin master --allow-unrelated-histories**
* **make some changes**: touch README.md
* **git status**: check the status
* **git commit -m 'message'**
* **git log**: check whether commit successfully
* **git push origin master**: push updates from local master branch to the origin remote

### Sync your github fork (copy from others)
* **git remote add upstream <url_of_original_repo>**
* **git remote -v**: check the remote status
* **git fetch upstream**: fetch updates from the upstream
* **git merge upstream/master**: merge upstream branch into our working branch in local machine
* **git push origin master**: push changes of local machine to origin repo in github website

### Updates rejected when pushing to github
* create a repo in github and initialize with a README file
* plan: make changes to local repo and get synced with the repo in github
* **mkdir test1**: create a dir in local machine
* **cd test1**: change directory to the sub-directory: 
* **git init**: Initialize git
* **git remote add origin <url_of_repo>**: Add remote that allows you easily reference your github layer
* Then make some changes in your local machine
* **git status**: confirm git has detected untracked file
* **git add .**: stage the file to be commited
* **git commit -m 'message'**: commit the changes
* **git push origin master**: which direct git to push the committed changes on the master branch to the origin that we defined earlier

Unfortunately, the push action is rejected since git detects the README file in github but not in your local machine. To fix the problem:
* **git pull origin master**, then **git push origin master**; if got `refusing to merge unrelated histories` problem, try **git pull origin master --allow-unrelated-histories**

Another two approaches to help you aviod this situation in the begining:
* 1. Do not create the README file when you create the github repo in the beginning
* 2. Using the cloning approach:(It automatically downloads the repo and stores it in a sub directory of your working directory; it also automatically sets up the origin remote so you don't have to add the remote manually; local repo and github repo are already in sync)
  * Create the repo with README
  * **git clone <url_of_repo>**
  * Make changes to local repo
  * **git add .**
  * **git commit -m 'message'**
  * **git push origin master**

### [Adding an existing project to GitHub using the command line](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)
* **git init**
* **git add .**
* **git commit -m "First commit"**
* **git remote add origin remote repository URL**
* **git remote -v**
* **git push -u origin master**

---

## 3.	These are common Git commands used in various situations:

1. start a working area (see also: git help tutorial)
* clone:	Clone a repository into a new directory
* init:		Create an empty Git repository or reinitialize an existing one

2. work on the current change (see also: git help everyday)
* add: 		Add file contents to the index
* mv:		Move or rename a file, a directory, or a symlink
* reset:	Reset current HEAD to the specified state
* rm:		Remove files from the working tree and from the index

3. examine the history and state (see also: git help revisions)
* bisect:	Use binary search to find the commit that introduced a bug
* grep:		Print lines matching a pattern
* log:		Show commit logs
* show:		Show various types of objects
* status:	Show the working tree status

4. grow, mark and tweak your common history
* branch:	List, create, or delete branches
* checkout:	Switch branches or restore working tree files
* commit:	Record changes to the repository
* diff:		Show changes between commits, commit and working tree, etc
* merge:	Join two or more development histories together
* rebase:	Reapply commits on top of another base tip
* tag:		Create, list, delete or verify a tag object signed with GPG

5. collaborate (see also: git help workflows)
* fetch:	Download objects and refs from another repository
* pull:		Fetch from and integrate with another repository or a local branch
* push:		Update remote refs along with associated objects


---

## 4. Markdown cheat sheet:

[README.md](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

![quick git command](https://github.com/StanleySongPro/github_tutorial/blob/master/quick_git_command.png "quick_git_command")





