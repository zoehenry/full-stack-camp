## Git Cheat Sheet
#### May 26, 2016
---

<!-- Note: Use this markdown file to take notes! -->
### Github Setup Resource

### Initial setup

#### First way,

1. Create a repo in Github
2. Create a repo in Github and copy the SSH url from
the `clone or download` dropdown.
3. `git clone` that repo

#### Second way,

Note: Let's use the convention that anything in `<>`
needs to be filled in with a name you pick.

1. `git init` in the folder you want to make a repo.
Usually, you want to start with an empty folder.
2. Create a repo in Github and copy the SSH url from
the `clone or download` dropdown.
3. `git remote add origin <github-url>`
4. `git fetch origin`

#### Basic Git Workflow

Now, say you're ready to make a change to your code.

1. `git checkout -b <branch-name>`
2. Make your changes to code.
3. From the root directory, `git add .`
4. `git status` to check all your files were added
correctly.
5. `git commit -v` or `git commit -m "<commit-message>"`
6. `git pull --rebase origin master` to put your commit
on top of the history of changes from the remote repo. (Note: first time, won't work, so skip step 6)
7. `git push origin <branch-name>`

#### Basic Git Merge Conflict Workflow

1. On your local machine, `git pull origin <branch-name>`
2. Then you attempt to merge master into it, `git pull origin master`
3. This will alert to a merge conflict, like so:
```
$ git pull origin master
Auto-merging
CONFLICT (add/add): Merge conflict in
Automatic merge failed; fix conflicts and then commit the result.
```
4. Run `git status` you should see something like this:
```
Unmerged paths:
	both added:      name-of-file.txt
```
5. Go open that file to see where the problem is,
look for `<<<<<< HEAD`. There can be multiple problems in each file.
6. Fix the conflicts. This requires some thought about
what the code means and what you intend to happen.
7. `git add name-of-file.txt`, check `git status`
and you'll see that it is no longer in the `unmerged paths`. Then `git commit -v` or `git commit -m "message"`. Then you can push `git push origin <branch-name>`.
8. Go back to Github and look at the updated pull request. You should be able to merge now.

#### Git Stash Workflow

1. Make some changes on your local machine, then run `git add <files>`. You can confirm those changes with
`git status`.
2. Then `git stash`. You can confirm your stash with `git stash list`.
3. Now, your current working directory should be clean. So you can pull `git pull origin master`.
4. And you can apply your git changes on top of master.
`git stash apply` or `git stash pop` if you want to delete them.


### Git Commands

#### Getting and creating projects
- `git init`
  Creates a new git repo in the current directory.
  If you provide a parameter, i.e. `git init foo`,
  it will create a new repo in that directory
- `git clone`
  You can grab the URL from Github, with the green dropdown `clone or download`, and paste that into
  your terminal, `git clone https://github.com/codesail-camp/full-stack-camp.git`
  If you provide a parameter, it will clone into
  that directory

#### Snapshots of your files
- `git add <filenames>`
  This adds the files to the "staging area", so that
  they can be committed. e.g. `git add .`
- `git status`
  This will tell you the status of the "staging area".
  So if files have or have not been added. If there
  are conflicts or not.
- `git diff`
  This will show the differences between your "current
  working directory" and the committed version of your
  branch. You want to run this before `git add`.
- `git commit`
    - `-m <git message>`
    - `-- amend`
      Amend means to rewrite history. It allows us
      to make changes to a commit that has already
      been committed.
- `git reset`
  This restores your current working directory to
  the last staged version.
- `git rm`
  This removes things from your staging area and
  restores them to your original committed version.
- `git mv`
  Does the same thing as `mv` but combines this with
  `git add`. Shorthand for `mv <file>` and `git add <file>`.
- `git stash`
  This creates a `WIP` staging area that can be retrieved at a later time. i.e. "restore point".
  - `git stash help` - This lists out all the options you can run on stash.
  - `git stash list` - Lists out all your stashes.
  - `git stash pop` - Restores your stash to your current working directory. But it also deletes from the stack.
  - `git stash apply` - Restores your stash to your current working directory. Leaves the stash on the stack.
  - `git stash show stash@{0}` - This will show the `diff` between your stash and your current working directory.

#### Branching and merging
- `git branch`
  - `-v`
  This tells you which branch you're currently on
  and all the branches on your computer.
- `HEAD`
  the `HEAD` branch is the current branch you've
  checked out on your local machine.
- `git checkout`
    - `-b`
  This will checkout a new branch, with `-b`, or an
  existing branch without it.
- `git merge`
- `git cherry-pick <commit>`
  This allows you to grab any commit from anyone's branch by its unique identifier (the hash)
  example: d56d732bfce475ede23b4ff809becefab0bda641

  `git cherry-pick d56d73`

#### Sharing and updating remote projects
- `git remote`
  This helps you manage your remote repos. So `origin` is the default repo and usually points to Github. You could also point to another person's computer or `fork`. `git remote add origin <github-url>`.
- `git fetch`
  Will update your local repo with all the new branches
  from the remote repo (Github). This will **not** merge
  these branches.
- `git pull <remote> <branch-in-remote>`
  git pull origin master
  It updates your local repo to match the repo on Github
  and it does an automatic, implicit `merge`
  It usually brings up VIM so you can write your
  commit message. Just use the default one and save it.

    - `-- rebase`
- `git push  <remote> <branch-in-remote>`
  It updates the Github repo to match your local repo.
  But if you haven't pulled first, and it's out of date
  it doesn't know how you want to merge, so it will fail.

    - `-f`

#### Inspection and comparison

- `git log`
  This shows the commit history in `less`, so that means
  you can scroll down with arrow keys or spacebar.
  If you run it with `git log -p` it also combines it
  with the diff.
- `git diff`
