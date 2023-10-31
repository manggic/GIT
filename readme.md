
## GIT all command

**git init** 
- This command turns a directory into an empty Git repository.
`git init` is like telling Git, "Hey, I want to use Git to keep track of changes in this folder," and it sets up the necessary structure and tools for you to start using Git to manage your project's versions.

**git clone <remote_URL>**
- To create a local working copy of an existing remote repository, use git clone to copy and download the repository to a computer. Cloning is the equivalent of git init when working with a remote repository. Git will create a directory locally with all files and repository history.<br>
```
git clone git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git
```

**git add <file_or_directory_name>**
- Adds files in the to the staging area for Git. Before a file is available to commit to a repository, the file needs to be added to the Git index (staging area). There are a few different ways to use git add, by adding entire directories, specific files, or all unstaged files.
``` 
# To add all files into staging area:
$ git add .

# To stage a specific file:
$ git add index.html

# To stage an entire directory:
$ git add css
```

**git commit -m "Commit message in quotes"**
- Record the changes made to the files to a local repository. For easy reference, each commit has a unique ID.
It’s best practice to include a message with each commit explaining the changes made in a commit. Adding a commit message helps to find a particular change or understanding the changes.
```
git commit -m "My first commit message"
```

**git status**
- It's provides a summary of the current state of your Git repository. It displays information about the files in your working directory, including whether they are untracked, modified, or staged for the next commit. Additionally, it shows the current branch you are on and informs you if you are ahead or behind the remote repository. 

**git config**
- git configuration allows you to customize your Git environment to suit your needs, such as specifying your name and email, setting up aliases for commonly used commands, configuring external text editors, and much more. These settings help Git work the way you want it to and can enhance your workflow when working with Git repositories.
```
# Running git config globally
$ git config --global user.email "my@emailaddress.com"
$ git config --global user.name "Brian Kerr"

# Running git config on the current repository settings
$ git config user.email "my@emailaddress.com"
$ git config user.name "Brian Kerr"
```

**git branch**
- To determine what branch the local repository is on, add a new branch, or delete a branch.
```
# Create a new branch
$ git branch <branch_name>

# List all remote or local branches
$ git branch -a

# Delete a branch
$ git branch -d <branch_name>

# Delete a branch forcefully
$ git branch -D [branch name]

# Delete a remote branch
$ git push origin --delete [branch name]
$ git push origin -d <branch_name>

```

**git checkout**
- It's use for 
  - Switch between branches.
  - Check out a specific commit to see the code at that point in time.`You are now in a "detached HEAD" state, meaning you're not on a branch but directly at the commit. You can review the code, test it, or compare it with the current state.`
  - Restore a file to a previous state.
```
# Check out the specific commit
$ git checkout <commit_id>

# After examining the code at the specific commit, making changes you want to go back to the feature-branch.
$ git checkout feature-branch

# Checkout an existing branch
$ git checkout <branch_name>

# Checkout and create a new branch with that name
$ git checkout -b <new_branch>

# Rename a local branch
$ git branch -m [old branch name] [new branch name]

# To discard all uncommitted changes in your working directory
$ git checkout .

# switch back to the branch you were on previously
$ git checkout -
```

**git merge**
- Integrate branches together. git merge combines the changes from one branch to another branch. For example, merge the changes made in a staging branch into the stable branch.
```
# Merge changes into current branch
$ git merge <branch_name>
```

**git remote**
- To connect a local repository with a remote repository. A remote repository can have a name set to avoid having to remember the URL of the repository.
```
# Add remote repository
$ git remote <command> <remote_name> <remote_URL>

# Adding a remote repository with the name of beanstalk
$ git remote add origin git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git

# List named remote repositories
$ git remote -v
```

**git pull <branch_name> <remote_URL/remote_name>**
- To get the latest version of a repository run git pull. This pulls the changes from the remote repository to the local computer.
```
git pull origin staging
```

**git push <remote_URL/remote_name> <branch>**
- Sends local commits to the remote repository. git push requires two parameters: the remote repository and the branch that the push is for.
```
# Push all local branches to remote repository
$ git push —all

# Push a specific branch to a remote with named remote
$ git push origin staging
```

**git show**
- This command in Git is used to display information about a specific commit. It provides detailed information about the changes made in the commit, including the commit message, the author, the date, and a unified diff of the changes made in that commit.


```
git show <commit>
```

**git stash**
- The git stash command saves your uncommitted changes (both staged and unstaged) away for later use, and then reverts them from your working copy.
You might use `git stash` if you want to temporarily switch branches without committing your changes to the current branch.


```
# This will save your changes to a local stash
$ git stash 
```

```
# List all of your stashed changes
$ git stash list
```

```
# To see changes made in a stash
$ git stash show -p <stash_name>
```

```
# To retrieve your stashed changes
$ git stash apply
$ git stash pop
```

```
# Clear all of your stashed changes
$ git stash clear
```

```
# Drop a specific stashed change
$ git stash drop <stash_name>
```

```
# To apply a specific stash, you can specify it by name
$ git stash apply stash@{1}
```

**git log**
- Displays a record of the commits in a Git repository.
By default, the git log command displays a commit hash, the commit message, and other commit metadata

```
# Show entire git log
$ git log

# Show one-line summary of each commit
$ git log --oneline
```

```
# To display the first 10 commits 
$ git log -10
```


**git reset**
- Git reset is a command that moves the current head of the branch back to a specified commit. This can be used to `undo commits that have not been pushed to a remote repository`.

```
$ git reset [options] <commit>

The options are:
1. --hard: This will reset the current branch to the specified commit and discard any uncommitted changes.
2. --soft: This will reset the current branch to the specified commit, but keep any uncommitted changes.
3. --mixed: This will reset the current branch to the specified commit, but keep any uncommitted changes that are not staged for a commit.

The commit can be a SHA-1 hash, a branch name, or a tag.
```

```
# To reset the current branch to the last commit
$ git reset --hard HEAD~1

# To reset the current branch to the master branch
$ git reset --hard origin/master

# To reset the current branch to the tag v1.0.0
$ git reset --hard v1.0.0
```

Note : `It is important to note that git reset is a local operation and does not affect the remote repository. If you have already pushed the commits that you want to undo, you should use git revert instead.`

**git revert**
- Git command that is used to create a new commit that undoes the changes made in a previous commit. This is a safe way to reverse changes without altering the project's commit history, making it a useful tool for fixing mistakes or undoing unwanted changes.


```
$ git revert <commit-hash>
```

**git reflog**
- Git command that stands for "reference log." It's a useful tool for tracking and recovering your project's history, including changes to branch references, commits, and other Git operations. The git reflog command displays a log of reference updates in your repository, helping you recover lost commits or branches.

```
git reflog
```

- <b>Recovering Lost Commits or Branches</b> :If you accidentally deleted a branch or lost a commit, git reflog can help you identify the reference or commit you want to recover.
For example, if you want to recover a deleted branch, you can use git reflog to find the commit hash before the branch was deleted, and then create a new branch using that commit hash.

```
git branch <new-branch-name> <commit-hash>
```

**git diff**
- Git command used to display the differences between various states of your Git repository. It allows you to compare changes between different commits, between the working directory and the staging area, or between different branches or commits. git diff is a powerful tool for reviewing and understanding the differences in your project's source code.

```
# Compare the current working tree to the last commit
$ git diff

# Compare the current working tree to the HEAD commit
$ git diff HEAD

# Compare the file `foo.txt` to the last commit
$ git diff foo.txt

# Compare the file `foo.txt` to the HEAD commit
$ git diff HEAD foo.txt

# Compare the branch `master` to the current working tree
$ git diff master

# Compare the branch `master` to the HEAD commit
$ git diff HEAD master

# Compare the changes between two specific commits
$ git diff <commit1> <commit2>

```

**git commit --amend**
- This command is a convenient way to modify the most recent commit. It lets you combine staged changes with the previous commit instead of creating an entirely new commit.

```
# change commit message of recently last commit
$ git commit --amend -m "an updated commit message"
```
- Let's say we've edited a few files that we would like to commit in a single snapshot, but then we forget to add one of the files the first time around. Fixing the error is simply a matter of staging the other file and committing with the --amend flag

```
# Edit hello.py and main.py
$ git add hello.py
$ git commit 
# Realize you forgot to add the changes from main.py 
$ git add main.py 
$ git commit --amend --no-edit
```
`The --no-edit flag will allow you to make the amendment to your commit without changing its commit message. The resulting commit will replace the incomplete one, and it will look like we committed the changes to hello.py and main.py in a single snapshot.`


### interactive rebase
- Interactive rebasing allows you to interactively rework your commit history before merging it into another branch.
- `Mind the word "local": it should only be used for cleaning up your own, local commit history, for example before integrating one of your feature branches into a team branch. In contrast, it should NOT be used on commit history that has already been pushed and shared on a remote repository. Interactive rebase is one of those tools that "rewrite" Git history – and you shouldn't do this on commits that have already been shared with others.`
- With interactive rebasing, you can:
     - Edit Commits: You can change commit messages, make small changes to the content of commits, or even split and combine commits.
     - Reorder Commits: Change the order of commits in your branch to provide a more logical and coherent history.
     - Squash Commits: Combine multiple commits into one, which is useful for collapsing a series of small, related commits into a single, more meaningful commit.
     - Drop Commits: Remove commits that you no longer want to include in your branch's history.
     - Resolve Conflicts: Just like a regular rebase, you'll need to resolve conflicts if they occur during the interactive rebase process.
- If we were talking about the very last commit, we could have simply used the --amend option of the git commit command 




[git advance topic link](https://youtu.be/qsTthZi23VE?si=vyB1BYmJjBI-9Ci0)
[interaction rebase doc](https://about.gitlab.com/blog/2020/11/23/keep-git-history-clean-with-interactive-rebase/)






