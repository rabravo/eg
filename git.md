# git

initialize a new repository

    git init


clone a repository

    git clone https://github.com/user/repo.git


clone a specific branch

    git clone -b main https://github.com/user/repo.git


show working tree status

    git status


stage a file

    git add file.txt


stage all changes

    git add .


commit staged changes

    git commit -m "message"


stage and commit all tracked files in one step

    git commit -am "message"


push to the remote

    git push origin main


pull (fetch + merge)

    git pull origin main


pull with rebase instead of merge

    git pull --rebase origin main



# Branching

create a new branch

    git branch feature-x


switch to a branch

    git switch feature-x


create and switch in one step

    git switch -c feature-x


list all branches (local and remote)

    git branch -a


rename the current branch

    git branch -m new-name


delete a local branch

    git branch -d feature-x


force-delete an unmerged branch

    git branch -D feature-x


push a new branch to origin

    git push -u origin feature-x


delete a remote branch

    git push origin --delete feature-x



# Merging and Rebasing

merge a branch into the current branch

    git merge feature-x


merge without a fast-forward (always creates a merge commit)

    git merge --no-ff feature-x


rebase current branch onto main

    git rebase main


interactive rebase — squash/edit/reorder last 3 commits

    git rebase -i HEAD~3


abort an in-progress rebase

    git rebase --abort


continue a rebase after resolving conflicts

    git rebase --continue



# Stashing

stash uncommitted changes

    git stash


stash with a description

    git stash push -m "work in progress"


list all stashes

    git stash list


apply the most recent stash (keeps it in the list)

    git stash apply


pop the most recent stash (removes it from the list)

    git stash pop


apply a specific stash

    git stash apply stash@{2}


drop a specific stash

    git stash drop stash@{0}



# Inspecting History

show commit log

    git log


show compact one-line log

    git log --oneline


show log as a graph with branches

    git log --oneline --graph --all


show changes introduced by each commit

    git log -p


show commits by a specific author

    git log --author="Alice"


show commits touching a specific file

    git log -- path/to/file.txt


show who changed each line of a file

    git blame file.txt


show the diff of uncommitted changes

    git diff


show the diff of staged changes

    git diff --staged


show changes between two commits

    git diff abc123 def456


show details of a specific commit

    git show abc123



# Undoing Changes

unstage a file (keep changes in working tree)

    git restore --staged file.txt


discard changes in the working tree

    git restore file.txt


undo the last commit, keep changes staged

    git reset --soft HEAD~1


undo the last commit, keep changes unstaged

    git reset HEAD~1


create a new commit that reverts a previous one

    git revert abc123


apply a specific commit from another branch

    git cherry-pick abc123



# Remotes and Tags

list remotes

    git remote -v


add a remote

    git remote add upstream https://github.com/original/repo.git


fetch from upstream without merging

    git fetch upstream


create a tag

    git tag v1.0.0


create an annotated tag

    git tag -a v1.0.0 -m "Release 1.0.0"


push all tags to origin

    git push origin --tags


delete a local tag

    git tag -d v1.0.0



# Searching

search for a string across all files in history

    git grep "search term"


find the commit that introduced a bug (binary search)

    git bisect start
    git bisect bad
    git bisect good v1.0


mark a commit as good or bad during bisect

    git bisect good
    git bisect bad


end the bisect session

    git bisect reset


