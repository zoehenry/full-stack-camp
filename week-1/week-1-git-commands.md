## Git Cheat Sheet
#### May 26, 2016
---

<!-- Note: Use this markdown file to take notes! -->
### Github Setup Resource

### Git Commands

#### Getting and creating projects
- `git init`
- `git clone`

#### Snapshots of your files
- `git add <filenames>`
this adds the files to the staging area so that they can be committed. `git add .`
- `git status`
this will tell you the status of the staging area. if files have or have not been added. if there are/nt conflicts.
- `git diff`
will show the differences between "current working directory" and the committed version of your branch. Note: you want to run this before `git add .`
- `git commit`
    - `-m <git message>`
    - `-- amend`
    Amend means to rewrite history. It allows us to make changes to a commit that has already been committed.
- `git reset`
restores your "current working directory" to last staged version.
- `git rm`
removes things from your staging area and restores them to your original committed version
- `git mv`
shorthand for `mv <file>` and `git add <file>`.

- `git stash`
this creates a `WIP` (work in progress) staging area that can be retrieved at a later time. i.e. "restore point" (like in video games). the file will disappear.
`git stash help`
this lists out all the options you can run on stash.
`git stash list`
lists out all your stashes.
`git stash pop`
restores your stash to your "current working directory" but also deletes the stash from the stack.
`git stash apply`
restores your stash to your CWD. leaves the stash on the stack.
`git stash show <stash-name>` use this after `git stash list` with the specific stash that you want. this will show the `diff` between your stash and your current working directory.
Stash is helpful if someone else has changed the master. you can stash your files, pull the new master, then pop your stash and push your changes.

#### Git Stash Workflow
1. make some changes on your local machine, then run `git add <files>`. You can confirm those changes with `git status`.
2. Then `git stash`. You can confirm your stash with `git stash list`.
3. Now, your current working directory should be clean. So you can pull `git pull origin master`.
4. And you can apply your git changes on top of master. `git stash apply` or `git stash pop` if you want to delete them.

#### Branching and merging
- `git branch`
  - `-v`
  this tells you which branch you're currently on and all the branches on your computer.
  `HEAD`
  the `HEAD` branch is the current branch that you've checked out on your local machine.
- `git checkout`
    - `-b`
    this will checkout a new branch, with `-b`, or an existing branch without it.
- `git merge`
- `git cherry-pick <commit>`
  This allows you to grab any commit from anyone's branch by its unique identifier the HASH. example: (d56d73...)

#### Sharing and updating remote projects
- `git remote`
This helps you manage your remote repos. So `origin` is the default repo and usually points to Github. You could also point to another person's computer or `fork`. `git remote add origin <github-url>`.
Note: fork a repo means you have a copy of the repo under your user. a fork is a copy of all the branches.
- `git fetch`
  Will update your local repo with all the new branches from the remote repo (Github). This will **not** merge
- `git pull <remote> <branch-in-remote>`
    - `-- rebase`
- `git push  <remote> <branch-in-remote>`
    - `-f`

#### Inspection and comparison

- `git log`
This shows the history of commits on your current branch.
- `git diff`

### Initial Setup - May 27

#### First Way

1. Create a repo in Github
2. Create a repo in Github and copy the SSH url from the `clone or download` dropdown.
3. `git clone` that repo

#### Second Way

Note: Let's use the convention that anything in `<>` needs to be filled in with a name you pick.

1. `git init` in the folder you want to make a repo. Usually, you want to start with an empty folder
2. Create a repo in Github and copy the SSH url from the `clone or download` dropdown.
3. `git remote add origin <github-url>`
4. `git fetch origin` to confirm that it worked

#### Basic Git Workflow

Now, say you're ready to make a change to your code.

1. `git checkout -b <branch name>` (Note: this is creating a branch)
2. Make your changes to code (like add a file).
3. From the root directory, `git add .`
4. `git status` to check all your files were added correctly.
5. `git commit -v` or `git commit -m "<commit-message>"`
6. `git pull --rebase origin master` to put your commit on top of the history of changes from the remote rep. (Note: The first time this won't work because there is no master to pull from.)
7. `git push origin <branch-name>` (Note: use this to push)

#### Basic Git Merge Conflict Workflow

1. `git pull origin <branch name>`
2. `git pull origin master`
3. this will alert to a merge conflict:
  message
4. `git status` like:
```
  unmerged paths:
  both added:   name-of-file.txt
```
5. Go open the file where the problem is, look for `<<<<< HEAD`. There can be multiple problems in each file.
6. Fix the conflicts. (requires some thoght about what the code means and what you want to happen. does order matter? do you need both?)
7. `git add name-of-file.txt` and then
8. `git status` you'll see no more `unmerged paths`
9. `git push origin <branch-name>`
10. Go back to GitHub and look at the updated pull request. You should be able to merge now.
