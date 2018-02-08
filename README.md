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

