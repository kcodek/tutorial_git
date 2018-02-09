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

#WORKING TOGETHER
LF in mac/Linux
CR in windows

LINE endings
#$ git config --global core.autocrlf input #changes CR/LF to LF on commit (on unix like systems)
#git config --global core.autocrlf true #changes LF to CR/LF on  checkout (on windows)

GIT attributes file

type  conversion settings
*     text=auto
*.jpg  binary
*.sh   text eol=lf
*.bat  text eol=crlf

CHERRY-PICK
#git checkout development
#git cherry-pick 8091a43(SHA)

Notice the SHA on the master and development are different after copy/
because it has a different parent on production branch

#git cherry-pic --edit 5321

#$ git cherry-pick --no-commit 32431df 34tfe44 
--no-commit pulls in changes and stages them but doesn't commit

#git  cherry-pick -x 5321 
-x adds source SHA to commit message
#git cherry-pick --signoff 5321
-signoff adds current user's name to commit message

SUBMODULES

#A git repo inside a Git repo
-pull down updates easily
-Test your changes with an actual dependent project
-share changes easily
-History independent of containing repo

#$ git submodule add git@example.com.:css.git
#$ git commit -m "Add CSS submodule"
#$ git push
#$ cat .gitmodules #config for submodules

to get the submodules, we need to initialize them
#$ git submodule init
#$ git pull

when there are new commits in the parent module
#$ git submodule update #code gets checked out head less
"Not currently on any branch"

creating a new branch with your most recent commit: "a7eded4". Name the branch temp_changes.
#$ git branch temp_changes a7eded4

You need to create a new branch from the commit with the SHA: 'a7eded4'. Try starting with the 'branch' git command.


#$ git merge temp_changes
#git merge a7eded4
& then
#push parent 

#Push twice when editing submodules
After finishing up a bunch of changes, you want to push them up to the remote so you can share it with your other co-workers that are working on the project. Since you're using submodules, you should make sure to use the option which checks whether you have un-pushed submodules.
# git push --recurse-submodules=check
 # aborts a push if you haven't pushed a submodule, run this from parent directory
We need to push submodule changes again. But this time, instead of going into the submodule to push it, just use the on-demand option for the --recurse-submodules option. This way submodules that need it will be pushed automatically.
#$ git push --recurse-submodules=on-demand

make it an alias
#git config alias.anything-you-want "push --recurse-submodules=on-demand"
#$ git config alias.pushall "push --recurse-submodules=on-demand"


#REFLOG
LOST DATA - after a hard reset
git keeps a second log in the local repo, called the reflog
#$ git reflog
#$ git reset --hard 123fkdkl #(from git reflog)
#$ git reset --hard HEAD@{1}

DELETED BRANCHES

ou decide to clean house a bit. You know that all branches have either been merged or abandoned, so you're going to delete them to keep a tidy repository. Go ahead and get started by deleting the fluffy_poodle branch.

# git branch -D fluffy_poodle
$ git log --walk-reflogs

$ git branch <newbranch_name> SHA
$ git branch <newbranch_name> HEAD@{1}


