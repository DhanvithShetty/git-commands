# Git Commands

To create an empty git repository and maintain the history of a project, use the command `git init` <br>
This will create a .git hidden folder that maintains the history of the project.

To list all the untracked/tracked files in the repository, use the command `git status` <br>
This will show you all the files that are either untracked or tracked(new/modified/deleted).

## How To Make Changes In Your Repository

To stage the changes, ie. track the changes made in the repository/project we use the command `git add`.
The . means that we will stage all the files in the project for tracking. The dot can be replaced by individual file names.
Eg: git add . OR git add main.py

To untrack a file that has already been staged, we use the command `git restore --staged file_name`
Eg: git restore --staged main.py

To maintain the changes/commit the changes we use the command `git commit -m "Enter msg here"`
Eg: git commit -m "Added main.py"

To check all the changes made in the project since the beginning, we use the command `git log`

To delete a file from the repo, we use the command `rm -rf file_name`
Eg: rm -rf main.py
git commit -m "Deleted main.py"

Need to learn how to get back to a certain commit in the past, didnt understand it well enough.

To link your local project to a github repo, we write the command `git remote add origin repo_url`
Eg:

To check what repo you are in we use `git remote -v`

To push your changes, we use the command `git push origin branch_name`
Eg: git push origin main

## How To Use Branches

To create a branch, we use the command: `git branch branch_name` <br>
Eg: `git branch new-feature`

To switch to a branch, we use the command `git checkout branch_name` <br>
Eg: `git checkout new-feature`

To do both in a single line, we can use the command: `git checkout -b branch_name` <br>
Eg: `git checkout -b new-feature` <br>
The `-b` flag signifies the creation of the new branch named `branch_name`.

The `git checkout branch_name` means that the HEAD pointer now points to `branch_name` which means that now the commits will be made to `branch_name` and not `main` branch.

To merge the changes made in a branch into the main branch, use the following set of commands:

```
git checkout main
git merge branch_name
```

Now, all the commits made in `branch_name` will be added to `main` branch.

## How To Work With Existing Repositories

To be able to make the changes you want to a repository that you don't have access to, you have to do the following steps:

Fork the repository on GitHub. <br>
This step creates a copy of the existing repository under your account using which now allows you to make changes to the copied repository.

To obtain the files from the copied repository, use the command: `git clone repo_url`
This step will create a folder in your pc that contains the files of the repository.

We can add the upstream url to our project using the command: `git remote add upstream repo_url`
The place from where you have forked the repository is known as upstream url.

## Pull Requests

**REMEMBER: 1 BRANCH = 1 PULL REQUEST**

To merge pull requests, head over to the Pull Requests Tab in the repository in GitHub and confirm the merge after checking the code.

After the pull request has been merged, the code in the main branch will now contain the newly made changes.

**The problem now is that the branch `main` of upstream has been updated but the branch `main` of the forked repo is not updated.** <br>

To update the branch `main` of the forked repo, we can use the following set of commands:

```
git checkout main
git fetch --all --prune
git reset --hard upstream/main
git push origin main
```

**RECOMMENDED**: We can also accomplish this by writing a single line, using the command:

```
git pull upstream main
git push origin main
```

## How To Combine Several Commits Into A Single Commit

Let us say that you have made several commits and `git log` shows multiple commits, to squash(combine) several commits, do the following:

Copy the hash of the commit where the **HEAD** pointer is.
Use the command: `git rebase -i commit's_hash`

You should now be able to see all the commits hash which has been reduced to a smaller size with the word pick.

To combine several commits into one, choose the commit that you want to appear in the log and let the keyword before the hash of that commit be **pick**.

Let all the other commit that you want to join into the **picked** commit be **squash**.

**Squash basically merges the corresponding commit to the previous pick.**

Escape out of the command and write `:x`. <br>
This lets you write a message for the commit
Escape out of the command and write `:x`. <br>

You can check out the merged commits in `git log`