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


#change the last commit
$ git commit --amend -m "New Message"


#adding a remote
$ git remote add origin https://github.com/kcodek/tutorial_git.git

$ git remote -v

$git push -u origin master  
