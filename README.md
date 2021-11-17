# Most common git commands

- `git init`
    - Initiate the time-machine
- `git status`
    - Check the status of changed or new files since the last `commit`
- `git add`
    - Tell git to start keeping tracking of a file/folder
- `git reset`
    - Tell git to "unprepare" (unstage) files that would be saved in a `commit`
- `git commit`
    - Make a "snapshot" of the current state of your files
- `git log`
    - See the history of your previous commits
- `git push/pull`
    - Send/retrieve changes from a remote repository (most commonly Github)

# Some handy more advanced commands

- `git stash`
    - Save any changed you've made to files git knows about *without* making a commit
- `git checkout commit/branch`
    - Use the time machine to hop to a specific commit or another timeline (branch)
    - `-b` will create a new branch and then switch to it
- `git branch`
    - For managing branches, e.g. `-D` will delete a branch
- `git merge`
    - Combine different timelines or snapshots together
    - `git pull` is actually combination of `git fetch` followed by `git merge`!
- `git rebase`
    - For *altering time* so you can pretend like you branched from earlier/later than you did or if you simply want to combine some commits together
    - Think of it like I want to establish a new "base" for my timeline

# Common workflows

## How do I see what files git is keeping track of?

- `git ls-tree -r branchName --name-only` will print all the files names git has been tracking

## I've been making changes to some old files and I also created some new ones and I want to commit them all

- `git add -u` will add all files that git was *already* tracking
- `git add -A` will add both tracked *and* new files
- `git commit -m "description of my changes"` take a snapshot  

## While I was working on one branch there were changes made to another branch and now I want to apply them to my current branch

```
(newbranch) # work work work
(newbranch) git commit -m "saving all my hard work"

Meanwhile...

(main) # More commits were made
(main) # More commits were made

I need to catchup!

(newbranch) git fetch main
(newbranch) git rebase main
```

## I was accidentally working on the wrong branch but I made a bunch of changes what do I do now?
- Don't `git commit`. Instead use `git stash` to temporarily save your changes
- `git checkout otherBranch` to switch to where you intended to be
- `git stash apply` to apply the changes you stashed
- Now you can proceed with `git commit` !

## I want to see what changes I made at some point in the past?
- Just use `git checkout commitHash` where `commitHash` will be a alpha-numeric string