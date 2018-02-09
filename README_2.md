#Advanced git commands

#alter commits in the SAME branch, -i interactive
git rebase -i HEAD~3 #(3 commits before current head)
- an editor pops up

git rebase -i HEAD 
# alters every commit AFTER the one specified - does nothing

git rebase -i HEAD^  # parent of the HEAD

#REORDER commits
git rebase -i HEAD~3

 #pick chooses a commit for replay, default script is in the chronological order
#swap the order of commits in editor

#REWORD
#enter a new message

#split commits
#EDIT -
..  replay changes, but stops without committing
after staging some code
git commit --amend
git rebase --continue

---- 
git reset HEAD^
# DO NOT specify --hard - files shall stay in the working directory

#SQUASH
enter the message for the new commit, save and exit

#####################################
STASHING
#$ git stash save 
# same as .. $ git stash

-- save to the temporary area & restore the state from the last commit

pushes the stash onto the stash stack - can have multiple stashes
#$ git stash list

#git stash apply 
# same as $ git stash apply stash@{0}
 - brings stashed files back
# git stash apply stash@{1}

stash has been applied but still it's there ..
#$ git stash drop  # discards a stash

#git stash pop
 - git stash apply & git stash drop


 in case of conflicts,.. commit your changes are merge them
 #$ git reset --hard HEAD
 #$ git stash apply

 if using pop, there's a conflict .. 
 the stash won't be dropped.. then manually drop it.

 #KEEP INDEX
 some changes to staging, some changes to stash
 #$ git stash save --keep index  
 #$ causes the staging area not to be stashed
 to restore  #git stash pop

#$ git stash save --include-untracked 
-- this option causes untracked files to be stashed too

#git stash list can take any option "git log" takes
#$ git stash list --stat

#show a particular stash
#$ git stash show stash@{0} 
#$ git stash show --patch # shows file diffs
#$ git stash save "Adding a stash message"


BRANCHING
#$ git stash branch gerbil-toys stash{0}
#$git stash branch 
checks a new branch out automatically & drops the stash automatically.
The new branch is an ordinary branch ready for commits







