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

