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

git stash show stash@{2} --patch

#$ git stash save "Adding a stash message"


BRANCHING
#$ git stash branch gerbil-toys stash{0}
#$git stash branch 
checks a new branch out automatically & drops the stash automatically.
The new branch is an ordinary branch ready for commits

#PURGING HISTORY
even if a file is deleted, its contents will still be visible in history.

TREE FILTER

#$ git filter-branch --tree-filter <shell command>
Git will check each commit out into working directory, run your command and re-commit

#--all  # filter all commits in all branches
#HEAD #filter only current branch

examples:
#remove passwords.txt
--tree-filter 'rm -f passwords.txt'

#doesn't fail if file isn't present
#git filter-branch --tree-filter 'rm -f passwords.txt' -- --all

#removes video files
--tree-filter 'find . -name "*.mp4" -exec rm {} \;' 

INDEX FILTER
# command must operate on a staging 

Remember, --index-filter will need a command that works on the staging area, which is going to be some sort of git command.

git will run the command against each commit but without checking it out first(so, it's faster)

--index-filter 'rm -f passwords.txt' # operates on working dir.

#$ git filter-branch --index-filter 'git rm --cached --ignore-unmatch master_password.txt'


--index-filter 'git rm --cached --ignore-unmatch passwords.txt' #operates on staging area, succeeds even if the file is not present



You must use the force (-f) to override the history backup for filter-branch.

#$ git filter-branch -f --tree-filter 'rm -f master_username.txt -- --all'


#$ git filter-branch -f --prune-empty -- --all
#prune empty option drops commits that don't alter any files








