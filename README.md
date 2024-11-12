# git note

check if git surveillance by checking .git file
```bash
ls -a
```
delete this hidden file could remove git surveillance
```bash
rm -rf .git
```
create a git local repo
```bash
git init my-repo
```
clone from remote repo, git covered by default
```bash
git clone <remote repo url>
```
git add from working area to staged area
status from untrack->staged
```bash
git add file.text 
git add *.text
git add .
```
discard files in staged area
```bash
git rm --cached file.text
```
commit staged files to local repo
```bash
git commit -m”” 
```
check commit log
```bash
git log
git log --oneline
```
reset commit version
```bash
git reset --soft # keep working and staged files
git reset --hard # remove all files from working and staged area
git reset --mixed # only keep working area files
```
check staged files
```bash
git ls-files
```
delete staged files
```bash
git rm --cached **filename.txt
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
only remove file in staged area
```bash
git rm --cached file.txt
```
#
in local git repo,  cd .shh
Ssh-keygen -t rsa -b 4096
enter return, to generate ssh key if it is first to config ssh



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
git checkout feature
git rebase main
```
