# github_tutorial

**version 1.0.0**

---
## 0. Terminology
* `Branches` are just labels associated to commits and they happen on single repository
* `Remote` are references of remote repo to local repo

## 1.	Command lines on github

* `git --version`:                check git version
* `git status`:                   check the status of local machine and remote repository
* `git help`:
* `git diff`:                     `working directory` & `staging area`
* `git diff --staged`:            `staging area` & `most recent commit`
* `git diff commit1 commit2`:     `commit1` & `commit2`
* `git diff branch1 branch2`:     `branch1` & `branch2`

* `git add <filename>`:           add new file or file with changes to github
* `git add -A`:                   add all to github
* `git add .`:                    add all to github
 
* `git commit -m 'messages'`:     new file or changes committed but still on local machine
* `git commit -a -m 'messages'`:  commit all the changes
* `git log`:                      get the history of all the commits or branch

* `git pull origin master`:       pull master branch from origin to the local branch we are working on
* `git push origin master`:       push changes in local branch we are working on to remote origin master branch

* `git clone github_url`:         download repo from the github, create connection through origin
* `git remote -v`:                viewing info about the remote repository
* `git branch -a`:                viewing info about the branch
* `git branch -av`:                viewing info about the branch
* `git branch -u bb/master`       重新调整local git repo track 哪一个remote，这里是track bb 的master branch
* `git remote add origin <url_of_repo>`: (if you don't have the origin)

* `git init`:                     initialize the local repo
* `rm -rf .git`:                  to remove the folder from git repository, to stop tracking this project on github

* `touch .gitignore`:             To create the list of files to ignore during version control
* `git reset <filename>`:         remove file in the staging area
* `git reset`:                    remove everything in the staging area

* `git fetch`:                    download a copy of remote repo to local `origin/master` bookmark
* `git fetch origin`:             update all the local copies from origin remote
* `git log origin/master` or `git diff origin/master master`: check out the local copies
* `git merge`:                    operates on commits 
* `git merge master origin/master`:   merge local `origin/master` with local master branch
* `git pull` = `git fetch` + `git merge master origin/master`

* `git checkout -b new_branch` = `git branch new_branch` + `git checkout new_branch`
* `git show commit_name`:             show the difference of this commit with its parent commit
* `git log --graph`:                  show the commits history graph
---

## 2.	[Github by tasks](https://www.youtube.com/watch?v=h1e8oC7g0Ps&index=11&list=PL5-da3qGB5IBLMp7LtN8Nc3Efd4hJq0kD):

### [Git quick reference for beginners](https://www.dataschool.io/git-quick-reference-for-beginners/)

### 1.Git configuration
* **git config --global user.name "Stanley Song"**
* **git config --global user.email "luge1123@gmail.com"**
* **git config --list**
* **git help config** or **git config --help**: so we can use `git add --help` as well

### 2.Copying a repo to your local computer
* **git clone <url_of_repo_others>**
* **git remote -v**: show the references connected to your repo
* **git branch -a**: check the branches locally and remotely
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

### 3.Sync your github fork (fork from others)
* **git clone < your-repo-URL >**
* **git remote add upstream <url_of_original_repo>**: 把原创作者加到上游
* **git remote -v**: check the remote status
* **git fetch upstream**: fetch updates from the upstream
* **git merge upstream/master**: merge upstream branch into our working branch in local machine
* 或者直接 **git pull upstream master**
* **git push origin master**: push changes of local directory to my origin repo in github website

### 4.Updates rejected when pushing to github
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

Another three approaches to help you aviod this situation in the begining:
* 1. Do not create the README file when you create the github repo in the beginning
* 2. Using the cloning approach:(It automatically downloads the repo and stores it in a sub directory of your working directory; it also automatically sets up the origin remote so you don't have to add the remote manually; local repo and github repo are already in sync)
    * Create the repo with README
    * **git clone <url_of_repo>**
    * Make changes to local repo
    * **git add .**
    * **git commit -m 'message'**
    * **git push origin master**
* 3. 或者
    * `git fetch origin`: update all the local copies of every branch for the origin remote
    * `git log origin/master`: inspect local copies
    * or `git diff origin/master master`: 看local origin/master与当前branch的difference
    * `git merge master origin/master`:  如果merge出现错误，手动解决错误，然后  add,commit etc...
    * **[`或者强行merge`](http://www-creators.com/en/archives/1687)**
        * `git fetch origin`: Fetch commits on "origin", and update all your remote tracking reference
        * `git reset --hard origin/master`: Force the local master to "origin/master"

### [5.Adding an existing project to GitHub using the command line](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)
* **git init**
* **git add .** : add files from working directory to staging area
* **git reset [file]** : if you want to unstage
* **git commit -m "First commit"**
* **git remote add origin remote_epository_URL** (所以先要在github创建repo)
* **git remote -v**
* **git push origin master**: push files in local master to remote origin (master branch)

### 6.Create git ignore
* **touch .gitignore**
* Open the `.gitignore` file with editor(sublime): subl .gitignore
* key in the list of files to ignore
    * `*.DS_Store`
    * `*.project`
    * `*.pyc`
    * `*.ipynb_checkpoints`
    * `*.spyproject`
    * `*Icon`
 
### [7.Apply gitignore on an existing repository already tracking large number of files](https://stackoverflow.com/questions/19663093/apply-gitignore-on-an-existing-repository-already-tracking-large-number-of-files)
* [Untrack files already added to git repository based on .gitignore](http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/)
* **git rm -r --cached .** : This removes everything from the index
* **git add .**
* **git commit -m ".gitignore is now working"**
* **git push -u origin master**

### 8.Fixing Common Mistakes and Undoing Bad Commits
* 1.如果对某一文件`calc.py`作出改变，但是我们不想要此改变，想 restore 到之前的状态
    * **git status**
    * **git diff**
    * **git checkout calc.py**
    
### 9.Working on branch
* **git checkout -b branch_name**
* **git add .**
* **git commit -m "changes you've made"**
* **git push -u branch_name**
* **git checkout master**
* **git pull --rebase**
* **git push -u origin master**

### 10.平时遇到问题总结
* 1.[Unable to push code to my private repo](https://community.atlassian.com/t5/Bitbucket-questions/Unable-to-push-code-to-my-private-repo/qaq-p/708507)
    * 报错: `repository access denied. access via a deployment key is read-only.fatal: Could not read from remote repository. Please make sure you have the correct access rights and the repository exists.`
    * 测试 `ssh -T git@bitbucket.org`: `authenticated via a deploy key. You can use git or hg to connect to Bitbucket. Shell access is disabled. This deploy key has read access to the following repositories: myName/repoName: xxxxxx -- my_email_address`
    * 解决:
        * 在这里真的是忍不住吐槽
        * Remove the SSH key from the repo. (Click on repo name > Settings > Access Keys)
        * Add SSH key to Account settings SSH keys. (Click on your avatar > Bitbucket Settings > SSH Keys)
* 2. 如果不小心 commit 了大文件， 采取以下步骤:
    * 删除github repo，并重新建立repo
    * add origin 来建立连接
    * git push -u origin master
    
* 3. [git push Out of memory, malloc failed:](https://stackoverflow.com/questions/8855317/git-push-out-of-memory-malloc-failed/26464366)
    * **git gc --auto --prune=today --aggressive**
    * **git repack**
    * **git config --global http.postbuffer 524288000**
    * **git config --global pack.windowMemory 256m**

### 程序猿 Common Workflow
#### Create a branch for desired feature
* `git branch calc-divide` : assumme we are editing a function within a python file **calc-divide**
* 或者加上 `-b`: `git branch -b calc-divide`
* `git checkout calc-divide` : now we are switching to work on this branch **calc-divide**, then we can make changes to the python file
* `git status`: take a look at the changes
* `git commit -m "Divide Function"`: push the changes to the staging area, this will have no effect on the local master brunch or remote repo
* `git diff --staged`: Optional, do this before commit, check the difference bettween the staging area and the most recent commit
#### After commit, push branch to remote
* `git push -u origin calc-divide`: `-u` tells git that we wanna associate the local **calc-divide** branch with the remote **calc-divide** branch, so in future we can just call `git pull` `git push` directly and git knows these branches are associated; 在这里，remote也自动创造了这个**calc-divide**的分枝
* `git branch -a`: check both local and remote branches
#### Merge a branch
* （local先merge， push之后remote也跟着merge）
* `git checkout master`: switch to work on master branch
* `git pull origin master`: 养成良好的从 remote pull 的好习惯
* `git branch merged`: check the branch we've merged so far
* `git merge calc-divide`: merge **calc-divide** with the local master branch
* `git push origin master`: after this, the remote **calc-divide** branch will merge with the remote master branch as well
#### Delete a branch
* `git branch merged`: check the branch we've merged once again
* `git branch -d calc-divide`: 砍掉local的分枝**calc-divide**
* `git branch -a`
* `git push origin --delete calc-divide`: 砍掉remote repo的分枝**calc-divide**
#### `A faster example`
* `git branch subtract`
* `git checkout subtract`: then make changes to `subtract`
* `git add .`
* `git commit -m "editing subtract"`
* `git push -u origin subtract`
* `git branch -a`
* `git checkout master`
* `git pull origin master`
* `git branch merged`
* `git merge subtract`
* `git push origin master`
* `git branch merged`
* `git branch -d subtract`
* `git branch -a`
* `git push origin --delete subtract`
---

## 4.	Udacity:
* `diff -u <file1> <file2>`
* [Concept Map: init, add, staging area](https://classroom.udacity.com/courses/ud775/lessons/2969618657/concepts/29605487710923)
* [Draw an updated diagram](https://classroom.udacity.com/courses/ud775/lessons/2969618657/concepts/29585087890923)
* [Concept Map: GitHub, Push, Pull, Remote](https://classroom.udacity.com/courses/ud775/lessons/3105028581/concepts/31546885350923)
---
## 4.	These are common Git commands used in various situations:

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

## 5. Markdown cheat sheet:
[Learn Markdown](https://guides.github.com/features/mastering-markdown/)

[README.md](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

![quick git command](https://github.com/StanleySongPro/github_tutorial/blob/master/quick_git_command.png "quick_git_command")
