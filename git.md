GIT commands
==============


Config
----------
### Set default editor to VIM
git config --global core.editor vim


Commits
--------------

### Update a commit
`git commit --amend`  

### Reset last commit
`git reset --soft HEAD^`  


Branches
--------------

### To cherry-pick
`git checkout branch_name`  
`git log`  
then get the sha1
`git checkout master`  
`git cherry-pick SHA1`  

### Update your branch from master
`git checkout branch_name`  
`git rebase master`  

### Rebase
`git pull --rebase origin master`  

### Resolve conflict on a rebase
`git add resolvedFile`  
`git rebase --continue`  
OR
`git rebase --abort`  

### Merge 2 branches
`git checkout master`  
`git merge branch_name`  

### Remove obsoletes local branches
`git remote prune origin`  

### On message 'your branch is 2 commits...'
`git fetch --depth=HEAD`  


Differences
--------------

### View changes in a file
`git log -p FILE`  

### View changes between head and a commit
`git diff SHA1`  

### View changes between 2 commits
`git diff SHA1 OTHER_SHA1`  

### View files that have changed between 2 branches
`git diff --name-status master..branch`  


Revert your changes
-------------------

### Revert a file
`git checkout -- FILE`  

### Revert a file to a specified state
git checkout SHA1 path/to/file.java

### Remove a file from staging area
`git reset FILE`  

### Reset your updates
`git reset --hard HEAD`  

### Reset to master on origin
`git reset --hard origin/master`  

### Cancel last commit
git reset HEAD^1

### Cancel a previous commit
`git rebase -i HEAD~2`  
`git mergetool`  
`git rebase --continue`  

### Remove a tag
`git tag -d TAGNAME`  

### if tag is already pushed, you should push the removal
`git push origin :refs/tags/TAGNAME`  


Working
--------------

### remove untracked files
`git clean -f`  

### Making a patch
git diff > your-patch

### Applying patch
git apply your-patch

### See graphical view of log
git log --graph --oneline --decorate

Bissect
--------------

### begin a bissection
`git bissect start`  
`git bissect bad COMMIT`  
`git bissect good COMMIT`  

### then, if you can, automate it
`git bissect run COMMAND`  

### after, you may log results
`git bisect log > bisect_log.txt`  

### and later, you may replay a log result
`git bisect replay bisect_log.txt`  


Update all local projects
--------------

`!/bin/bash`  
`command='git pull'`  
`for i in `ls -d */`; do`  
`   echo Udating ${i}`  
`   cd ${i}`  
`   $command`  
`   cd ..`  
`done`  
