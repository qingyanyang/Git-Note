# git note

check if git surveillance by checking .git file
```git
ls -a
```
delete this hidden file could remove git surveillance
```git
rm -rf .git
```
create a git local repo
```git
git init my-repo
```
clone from remote repo, git covered by default
```git
git clone <remote repo url>
```
git add from working area to staged area
status from untrack->staged
```git
git add file.text 
git add *.text
git add .
```
discard files in staged area
```git
git rm --cached file.text
```
commit staged files to local repo
```git
git commit -m”” 
```
check commit log
```git
git log
git log --oneline
```
reset commit version
```git
git reset --soft // keep working and staged files
git reset --hard // remove all files from working and staged area
git reset --mixed // only keep working area files
```
check staged files
```git
git ls-files
```
delete staged files
```git
git rm --cached **filename.txt
```
compare diffs
```git
git diff
git diff HEAD
git diff cached
git diff 56476547 7625375
```
remove files in both working and staged area
```git
git rm file.txt
```
only remove file in staged area
```git
git rm --cached file.txt
```
#
in local git repo,  cd .shh
Ssh-keygen -t rsa -b 4096
enter return, to generate ssh key if it is first to config ssh

add remote url to local repo
```git
git remote add <remote shortname><url>
// shortname: origin
// url: git@github.com.jshdkjshkjdhksjsdjshdg****
// example: git remote add origin git@github.com.kusgjagtsdyjs
```
push to remote repo
```git
git push -u <remote shortname><remote branchname>:<local branchname>
remote shortname: origin
remote branchname: main
local branchname: main
```

pull remote branch to local branch, this will excute merge after pulling code
```git
git pull origin main:main
```
if conflicts
```git
git fetch
(main) git merge dev
```
branch commands
```git
git branch branchname
git checkout branchname
git switch branchnam // better use this
```
check brancg graph
```git
git log --graph --oneline --decorate --all
```
delete branch
```git
git branch -d dev // -d: delete branch that has been merged already
git branch -D dev // -D: force to delete branch
```
stage + commit
```git
git commit -a -m “feat: ***”
git commit -am “feat: ***”
```
Git rebase
```git
git checkout feature
git rebase main
```
