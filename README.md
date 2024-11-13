# git note

## config
check version
```bash
git --version
```
config user name and email, this info will be shown at some senarioes: pr, commits
```bash
git config --global user.name "Chelsea.Y"
git config --global user.email "yangqingyan0@gmail.com"
# check configs
git config --global --list

# locally config eg: in a school project folder
git config user.name "Qingyan Yang"
git config user.email "a1865304@adelaide.edu.au"
git config --list
```
## set up
create a git local repo
```bash
git init (my-repo)
```
clone from remote repo, git covered by default
```bash
git clone <remote repo url>
```
check if git surveillance by checking .git file
```bash
ls -a
```
delete this hidden file could remove git surveillance
```bash
rm -rf .git
```

## Scenario:

In Git, we have three main areas in the local environment:
	1. Working Directory: Where your files are created and edited.
	2. Staging Area: Where changes are staged and prepared for committing.
	3. Git Repository: Where commits are stored in your local repository.

Additionally, we have the:
	1. Remote Repository: Such as a GitHub repository, where the code is synchronized and shared.

## Situation:

I added all untracked files from the working directory to the staging area, committed them to my local Git repository, and pushed the commit to the remote GitHub repository. Later, I realized I had mistakenly uploaded a file that should have been ignored using .gitignore.

## Analysis:
	1. Working Directory: The files remain unchanged.
	2. Staging Area: The staging area is now clean after the commit.
	3. Local Git Repository: Contains the new commit with all tracked files.

git rm --cached removes the file from tracking but keeps it in the working directory. After adding it to .gitignore and untracking it, future git add commands will ignore this file, and it won’t be included in new commits.

Commands to Check File Status
Check Staging Area and Untracked/Modified Files:
```bash
git status
```
Check Tracked Files in the Repository:
```bash
git ls-files
```

## Solution:
1. Add the File to .gitignore: Ensure the file will be ignored in the future but remains in the working directory.
2. Untrack the File:
```bash
git rm --cached <file-path>
```
3. Commit the Changes:
```bash
git commit -m "Remove file from tracking and add to .gitignore"
```
4. Push to Remote Repository:
```bash
git push origin <branch-name>
```
## tracked vs staged
Difference Between Staged and Tracked in Git

	1.	Tracked:
	•	A tracked file is any file that Git is aware of and is monitoring for changes. This includes files that have been committed at least once to the Git repository.
	•	Tracked files can be in one of three states:
	•	Unmodified: The file hasn’t changed since the last commit.
	•	Modified: The file has changed in the working directory but hasn’t been staged yet.
	•	Staged: The file has been modified and added to the staging area, ready to be committed.
	2.	Staged:
	•	A staged file is a file that has been added to the staging area using git add. This means it is ready to be included in the next commit.
	•	When you stage a file, Git takes a snapshot of it and prepares it to be committed to the local repository.
	•	Staging allows you to control which changes will be committed, making it possible to commit only a subset of the changes in your working directory.

 Example

	1.	You create a new file called example.txt:
	•	Initially, it is untracked.
	2.	You run git add example.txt:
	•	example.txt becomes staged and is now a tracked file.
	3.	You make changes to example.txt but don’t run git add again:
	•	The file is tracked and modified but not staged.
	4.	You run git add example.txt again:
	•	The modified changes are staged.
 
## Add
This command stages all changes, including deletions, modifications, and new files
```bash
git add file.text 
git add *.text
git add .
```
undo changes in the staging area, but keep changes in working directory
just like undo 'git add'
```bash
git reset
```
before add ., some changes happen at working directory, but these changes can be done by click discard changes in vs code
undo untrack files
```bash
git clean
```
undo tracked modifications
```bash
git checkout .
```
undo commit, but changes still kept in staging area
```bash
git reset --soft HEAD~1
```
undo commit and add . but still want to keep the changes in your working directory
```bash
git reset --mixed HEAD~1
```
revert to last commit and will not save the changes unlike 'git stash'
```bash
git reset --hard
```

## stash
git stash temporarily saves your uncommitted changes (both staged and unstaged) and reverts your working directory back to the state of the last commit. 
```bash
git stash

# check stashes
git stash list
# apply last stash but not delete it
git stash apply (--index)
# apply last stash and delete it
git stash pop
# delete last stash
git stash drop
# clear all stashes
git stash clear
```
## revert
used to undo a commit by creating a new commit that reverses the changes made by the specified commit
```bash
git revert 
```
check commit log
```bash
git log
git log --oneline
```
compare diffs
```bash
git diff
git diff HEAD
git diff cached
git diff 56476547 7625375
```
remove files in both working and staged area
```bash
git rm file.txt
```

## remote

origin vs upstream
```bash
https:blog.csdn.net/weixin_37646636/article/details/129778632
```
remote repo (eg: github)
```bash
git remote add <remote shortname><url> # eg: git remote add origin https:# github.com/user/repo.git
git remote rm <remote shortname>
git remote rename old-name new-name

git remote -v # list remote repos

# eg:
# origin  https:# github.com/user/repo.git (fetch)
# origin  https:# github.com/user/repo.git (push)
```
delete a branch from remote
```bash
git push origin --delete <branch-name>
```
push to remote repo
```bash
git push -u <remote shortname><remote branchname>:<local branchname>
git push # push local changes to tracked remote repo
git push --force # after local reset, the remote one will head few commits, use force to forcely cover remote content
```
update remote changes to local remote info
```bash
git fetch <remote shortname> <branch-name>
```
git pull Without Specifying Branch: fetch and merge changes from tracked remote repo(current branch tracked) into current repo
```bash
git pull
```
git pull with Specifying Branch: fetch changes from specific remote branch into local remote, and merge this change into current local branch
```bash
git pull origin/branch-name

# eg:
# git pull origin main (this happens before pull request)
```
pull remote branch to loacl
```bash
git checkout origin/branch-name 
```
check which remote branch my current branch is tracking with
```bash
git branch -vv
```
change my remote tracking
```bash
git branch --set-upstream-to=origin/feature-branch
```

## branch
list all branches
```Python
git branch # local branches
git branch -r # remote branches
```

create new branch
```bash
git branch <new-branch-name> # but not switch to it
git checkout -b <new-branch-name> # and switch to it
git checkout/switch <branch-name> # switch to a existing branch
```
change branchname
```bash
git branch -m <new-branch-name> # will change current local name to new one
git branch -m <old-branch-name> <new-branch-name> # if you are on different branch
```
delete local branch
```bash
git branch -d <branch-name> # -d: delete branch that has been merged already
git branch -D dev # -D: force to delete branch
```
## rebase
```bash
# switch to main and pull the latest changes
git switch main
git pull origin main
# merge main to feature branch and resolve conflicts 
git switch feature
git rebase main
# add to staged and push to remote
git add .
git rebase --continue
git push (--set-upstream origin feature)
# then create pr on github
# after code reviewing done, do rebase and merge quickly!
```
