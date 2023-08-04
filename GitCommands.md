# Git Commands

To create an empty git repository and maintain the history of a project, use the command `git init` <br>
This will create a .git hidden folder that maintains the history of the project.<br>

To list all the untracked/tracked files in the repository, use the command `git status` <br>
This will show you all the files that are either **untracked or tracked(new/modified/deleted)**.<br>

## <u>How To Make Changes In Your Repository</u>

To stage the changes, ie. track the changes made in the repository/project we use the command `git add`.<br>
The . means that we will stage all the files in the project for tracking. The dot can be replaced by individual file names.<br>
Eg: git add . OR git add main.py<br>

To untrack a file that has already been staged, we use the command `git restore --staged file_name`<br>
Eg: git restore --staged main.py<br>

To maintain the changes/commit the changes we use the command `git commit -m "Enter msg here"`<br>
Eg: git commit -m "Added main.py"<br>

To check all the changes made in the project since the beginning, we use the command `git log`<br>

To delete a file from the repo, we use the command `rm -rf file_name`<br>
Eg: rm -rf main.py<br>
git commit -m "Deleted main.py"<br>

To go back to a particular commit, use `git reset --hard commit_hash_id`. <br>
The hash ID is found from `git log`.<br>
This command **<u>deletes any changes</u>** made after the specific commit. <br>

To link your local project to a github repo, we write the command `git remote add origin repo_url`<br>
Eg: git remote add origin https://github.com/DhanvithShetty/git-commands.git <br>

To check what repo you are in we use `git remote -v`<br>

To push your changes, we use the command `git push origin branch_name`<br>
Eg: git push origin main<br>

## <u>How To Use Branches</u>

To create a branch, we use the command: `git branch branch_name` <br>
Eg: `git branch new-feature`<br>

To switch to a branch, we use the command `git checkout branch_name` <br>
Eg: `git checkout new-feature`<br>

To do both in a single line, we can use the command: `git checkout -b branch_name` <br>
Eg: `git checkout -b new-feature` <br>
The `-b` flag signifies the creation of the new branch named `branch_name`.<br>

The `git checkout branch_name` means that the HEAD pointer now points to `branch_name` which means that now the commits will be made to `branch_name` and not `main` branch.<br>

To merge the changes made in a branch into the main branch, use the following set of commands:<br>

```
git checkout main
git merge branch_name
```

Now, all the commits made in `branch_name` will be added to `main` branch.<br>

## <u>How To Work With Existing Repositories</u>

To be able to make the changes you want to a repository that you don't have access to, you have to do the following steps:<br>

Fork the repository on GitHub. <br>
This step creates a copy of the existing repository under your account using which now allows you to make changes to the copied repository.<br>

To obtain the files from the copied repository, use the command: `git clone repo_url`<br>
This step will create a folder in your pc that contains the files of the repository.<br>

We can add the upstream url to our project using the command: `git remote add upstream repo_url`<br>
The place from where you have forked the repository is known as upstream url.<br>

## <u>Pull Requests</u>

**<u>REMEMBER: 1 BRANCH = 1 PULL REQUEST</u>**

To merge pull requests, head over to the Pull Requests Tab in the repository in GitHub and confirm the merge after checking the code.<br>

After the pull request has been merged, the code in the main branch will now contain the newly made changes.<br>

**The problem now is that the branch `main` of upstream has been updated but the branch `main` of the forked repo is not updated.** <br>

To update the branch `main` of the forked repo, we can use the following set of commands:<br>

```
git checkout main
git fetch --all --prune
git reset --hard upstream/main
git push origin main
```

**RECOMMENDED**: We can also accomplish this by writing a single line, using the command:<br>

```
git pull upstream main
git push origin main
```

## <u>How To Combine Several Commits Into A Single Commit</u>

Let us say that you have made several commits and `git log` shows multiple commits, to squash(combine) several commits, do the following:<br>

Copy the hash of the commit where the **HEAD** pointer is.<br>
Use the command: `git rebase -i commit's_hash`<br>

You should now be able to see all the commits hash which has been reduced to a smaller size with the word pick.<br>

To combine several commits into one, choose the commit that you want to appear in the log and let the keyword before the hash of that commit be **pick**.<br>

Let all the other commit that you want to join into the **picked** commit be **squash**.<br>

**Squash basically merges the corresponding commit to the previous pick.**

Escape out of the command and write `:x`. <br>
This lets you write a message for the commit.<br>
Escape out of the command and write `:x`. <br>

You can check out the merged commits in `git log`<br>

## <u>What Are Merge Conflicts And How To Resolve Them</u>

A Merge Conflict occurs when you or any of your team members make **conflicting changes** to the same file from two different branches.<br>

A sample scenario of a merge conflict could look like this:

You work in branch `main` and you make changes to line 1 of a `mytext.txt` file, say Hi World.<br>

You switch to branch `new-feature` and you make a change to the same line two of `mytext.txt`, say Hello Earth.<br>

If you **attempt to merge** the branch `new-feature` to `main`, Git won’t be able to automatically decide which one to accept between **Hi World** and **Hello Earth**. So, Git will raise a **merge conflict error** and tell you to **<u>manually resolve the conflict</u>** and you can do so using GitHub.

## <u>Additional Resources:</u>

**[Understand Merge Conflicts Better](https://www.freecodecamp.org/news/how-to-fix-merge-conflicts-in-git/#whatisamergeconflictingit)**

**[Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)**