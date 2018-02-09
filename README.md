# tutorial_git
git practice

gitreally!
really really git!

#git commands

#undo last commit, put changes in staging
$ git reset --soft HEAD^  

#undo last commit and all changes
$ git reset --hard HEAD^  

#undo last two commits and all changes
$ git reset --hard HEAD^^  

<!-- fatal: ambiguous argument 'HEAD^^': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions -->



#change the last commit
$ git commit --amend -m "New Message"


#To add new remotes
# $ git remote add <name> <address>

#To remove  remotes
# $ git remote rm <name>

#To push to remotes, -u : usually 
#$ git push -u <name> <branch>

#Use git checkout to undo changes done to cats.html and index.html
#$ git checkout -- cats.html index.html


$ git remote add origin https://github.com/kcodek/tutorial_git.git

$ git remote -v

#remote repo name - origin, local branch to push - master
$git push -u origin master  

#commit without the staging area,
#$ git commit -a -m "banner" index.html


#create a branch
#$ git branch cat

#remove a branch
#$ git branch -d cat

#admin feature - creates and checks out branch
#$ git checkout -b admin

#what git pull does internally
1. Fetch(or Sync) our local repository with the remote one - $git fetch
2. Merges the origin/master with master $ git merge origin/master

Conflict
Commit editor

#list all remote branches
#git branch -r   

#$git remote show origin 

#delete remote branch
#$ git push origin :shopping_cart

#must delete the local branch manually
#$git branch -d shopping_cart

#$git remote prune origin

#heroku deploys only from master
#$git push heroku-staging staging:master

Tagging - a tag is ref to a commit
#$git tag
#$git tag -a v0.0.3 -m "version 0.0.3"
#$git push --tags 

#git checkout v1.3.1

Specify a remote to see specific information about that remote. The git remote command will show you available remotes.

$ git remote show origin

You still have a stale local branch tracking the now-deleted origin/weasel. Clean up your local references.git


#$git fetch

#git rebase
1. Move all changes to master which are not in master to temporary area
2. Run all origin/master commits
3.Run all commits in the temporary area, one at a time

if there are conflicts while rebase
#$"git rebase --continue"
#$ git rebase --skip
#$ git rebase --abort

While pull might work, I want you to retrieve the changes without merging them. Pull will automatically merge the changes, use fetch instead.
so use git fetch instead
#$git fetch

Now run another rebase to move your commit after the latest fetched one.

#$ git log --pretty=oneline
#$ git config --global color.ui true  
#$ git log --pretty=format:"%h %ad- %s [%an]"   
#$ git log --oneline -p        
#$ git log --oneline --stat
#$ git log --oneline --graph             
#  git log --until=1.minute.ago
#   git log --since=1.day.ago
#   git log --since=1.hour.ago
#   git log --since=1.month.ago --until=2.weeks.ago
#   git log --since=2018.01.01 --until=2018.02.08


get a diff that includes the previous commit, as well as its parent.
# git diff HEAD~2
 #  git diff HEAD^ #parent of latest commit
 #  git diff HEAD^^ #grandparent of latest commit
 #  git diff HEAD~5 # five commits ago
 #  git diff HEAD^..HEAD #second most recent commit vs. most recent

#git log --oneline
    b200d73 (HEAD -> master) log pretty
    05a597d fetch and rebase
#git diff b200d73 05a597d

Bring up a summary of file changes.


Use the -p option(--patch) to display diff changes in the output included in the log.
#git log -p



#git diff master shopping_cart
#git diff --since=1.week.ago --until=1.minute.ago 
#git blame README.md --date short
Use git blame to see the annotated source, so you can figure out who made all these changes


Excluding files
.git/info/exclude  - list the folder to exclude it from git

.gitignore - don't commit log files
logs/*.log  - from logs folder no .log file

#$ git rm readme.txt
#$ git status
#$ git commit -m "Remove readme.txt"

stop watching the changes
#$ git rm --cached development.log
#$ git add .gitignore
#$ git commit ... 

#git config --global user.name "kcodek"
#git config --global user.email "a@gmail.com"
#git config --global core.editor emacs
#git config --global merge.too opendiff
#git config --list

# $git config user.email "admin@example.com"
# for the current repo

git config --global alias.mylog \
"log --pretty=format: '%h %s [%an]' --graph"

git config --global alias.lol \
"log --graph --decorate --pretty=oneline --abbrev-commit --all"

git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit 

 


