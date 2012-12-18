GIT commands
==============

Config
----------
### Set default editor to VIM
`git config --global core.editor vim`

### Set colors 
`git config color.ui true`


Commits
--------------

### Update a commit
`git commit --amend`

### Reset last commit
`git reset --soft HEAD^`

### Reset to origin 
`git reset --hard origin/master`  

### Push a single commit
`git push origin SHA1:master`


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

### Remove local branch
`git branch -d branch-name`  

### Remove remote branch
`git push origin :branch-name`  

### Copy content from a branch to another
`git checkout BRANCH -- path/to/file.ext`

### Show merged branch
`git branch --merged`

### Show non merged branch
`git branch --not-merged`

### Show what branch contains that commit
`git branch --contains SHA1`


Search
--------------

### Search last matched commit search
`git show :/query`

### Search what commit has changed that String
`git log -GsearchedString`


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

### View changes between your branch and remote branch 
`git diff master origin/master` 

### Blame ignoring whitespace
`git blame -w`

### Blame detecting code moves 
`git blame -M`

### Blame detecting code moves between files
`git blame -C`

### Blame detecting code moves between files and in all commits
`git blame -CCC`

Revert your changes
-------------------

### Revert a file
`git checkout -- FILE`  

### Revert a file to a specified state
`git checkout SHA1 path/to/file.java`

### Remove a file from staging area
`git reset FILE`  

### Reset your updates to your local head
`git reset --hard HEAD`  

### Reset to master on origin
`git reset --hard origin/master`  

### Cancel last commit
`git reset HEAD^1`

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

### Better git status
`git status -sb`

### remove untracked files
`git clean -f`

### call git rm on deleted files
`gst -s | grep ' D ' | cut -f3 -d' ' | xargs git rm`

### Making a patch
`git diff > your-patch`

### Applying patch
`git apply your-patch`

### See graphical view of log (where X is max number of commit)
`git log --graph --oneline --decorate -n X`

### Remove a file from repository
`git filter-branch --tree-filter 'rm -f file-to-remove' HEAD`

### Find lost commits
`git fsck --lost-found`

Bissect
--------------

### begin a bisection
`git bisect start`  
`git bisect bad COMMIT`  
`git bisect good COMMIT`  

### test, then
`git bisect good`
or 
`git bisect bad`

### or, if you can automate it
`git bisect run COMMAND`  

### after, you may log results
`git bisect log > bisect_log.txt`  

### and later, you may replay a log result
`git bisect replay bisect_log.txt`  


Update all local projects
--------------

``!/bin/bash``

``for i in \`ls -d */\`; do``

`` (echo Udating ${i} && cd ${i} && git pull --rebase)``
 
``done``


Alias
------

### Open current project on github from command line
`alias gitweb="git config --get remote.origin.url | sed -e 's/^.*github\.com./https:\/\/github.com\//' | sed -e 's/\.git$//' | xargs python -m webbrowser -t > /dev/null"`
