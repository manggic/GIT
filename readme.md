
## GIT all command

**git init** 
- This command turns a directory into an empty Git repository.
`git init` is like telling Git, "Hey, I want to use Git to keep track of changes in this folder," and it sets up the necessary structure and tools for you to start using Git to manage your project's versions.

**git clone <remote_URL>**
- To create a local working copy of an existing remote repository, use git clone to copy and download the repository to a computer. Cloning is the equivalent of git init when working with a remote repository. Git will create a directory locally with all files and repository history.<br>
```
git clone git@account_name.git.beanstalkapp.com:/acccount_name/repository_name.git
```

**Obtain only the remote URL**
```
$ git config --get remote.origin.url
$ git remote show origin
```
**How to ungit a directory?**
```
Try removing the .git directory and .gitignore if exist: rm -Rf .git .gitignore
```

**To check git config**
```
$ git config --list
$ git config -l
```

**To get the date when a repository was first built?**
```
$ git show $(git log --oneline | tail -n 1 | cut '-d ' -f 1) | grep '^Date:'
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
# List all local branches 
$ git branch

# List both local and remote branches
$ git branch -a

# List remote branches from the remote repository
$ git branch -r

# Create a New Branch from a Specific Commit
$ git branch <new-branch-name> <commit-hash>

# Create a new branch
$ git branch <branch_name>

# Create and Switch to a New Branch
$ git checkout -b <new-branch-name>

# Rename a Branch
$ git branch -m <new-branch-name>

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
# reset to a commit id ( changes comes under staged ) 
$ git reset --soft <commit-id>

# reset to previous commit-id ( changes are unstaged )
$ git reset HEAD~1
```

```
# NOTE : subsequent commits will be completely gone in case of hard reset

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

**git reflog** (reference log)
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

**git rebase**
- Git rebase is a way to integrate changes from one branch into another while making it appear as if those changes were made on top of the current branch. It's like taking the changes from one branch and putting them on top of another branch's changes.

```
git checkout feature
git rebase main
```
- This takes the changes from the feature branch and applies them on top of the latest commit in the main branch.

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


```
# commit id will be of before the commit_id where need to be changed (just below the target commit id)
$ git rebase -i <commit_id> 
```
![change_old_commit_msg](/images/change_the_commit_msg_1.png)
![change_old_commit_msg](/images/change_the_commit_msg_2.png)
![change_old_commit_msg](/images/change_the_commit_msg_3.png)
<b>For changing old commit msg : </b>
`
An editor window will now open, containing a list of the commits that you just selected for manipulation.
One other important thing to note about this editor window: you don't perform the actual manipulations here! Or, in this concrete example, you do NOT go ahead and change the commit message here. Instead, you only mark the commit you want to change with an action keyword. In our case, because we want to change a commit’s message, we mark the line with "reword". If you then save and close this editor window, a new one will open, containing the old commit’s message. Now is the time to finally make your changes
`

![combining_multi_commit_into_single](/images/combining_multi_commit_into_single_1.png)
![combining_multi_commit_into_single](/images/combining_multi_commit_into_single_2.png)
![combining_multi_commit_into_single](/images/combining_multi_commit_into_single_3.png)
<b>For merging many commit into single commit : </b> 
`
Again, an editor window will open, listing that part of our commit history that we want to manipulate:
The action keyword we are going to use here is called "squash." And there's only one important piece of information you need to know about squash in order to use it: the line we mark up with the "squash" keyword will be combined with the line directly above. That’s why, as you can see in my screenshot above, I’ve marked line #2 with "squash" in order to combine it with line #1.
We can now save and close the editor window and again watch and a new window appear: we are now asked to provide a commit message for the new commit that is created when combining those two old ones.
`


**git cherry-pick**
- The "cherry-pick" command is a Git feature that allows you to pick and apply specific commits from one branch to another. It's a useful tool when you want to select specific changes from one branch and apply them to another without merging the entire branch. Cherry-picking is often used when you want to apply specific bug fixes or features from one branch to another, and you don't want to bring in all the changes from the source branch.

```
# switch to branch in which u want to fetch the changes
$ git checkout <branch_name>

# commit_id of the branch u want to pick the changes
$ git cherry-pick <commit_id>

# to abort after getting conflicts during a cherry-pick operation
$ git cherry-pick --abort

# fetch multiple commits from one branch and apply them to another
$ git cherry-pick <commit-hash-1> <commit-hash-2> <commit-hash-3>

```

- if u get conflict while cherry pick, u can resolve it and add it into staging
```
git add filename
```  
- After resolving the conflict and staging the changes, you can continue the cherry-pick operation using the following command
```
git cherry-pick --continue
```

- To remove the commit from the source branch
```
$ git checkout source-branch
$ git reset --hard HEAD~1
```
`The HEAD~1 refers to the commit before the last one, effectively removing the last commit from the branch.`

```
# To check what's inside proj config 
$ cat .git/config
```

**git submodule**
- Git submodules are a way to include one Git repository as a subdirectory inside another Git repository.
Submodules are useful when you want to incorporate external code or libraries into your project while keeping those components in their separate repositories and versions.
Git records information about the submodule, such as its URL and the path where it's located within your repository. This information is stored in a file named .gitmodules in the root of your repository.

```
# Adds a submodule to your repository
$ git submodule add <repository_url>

# Clones a repository with submodules, ensuring that the submodules are also cloned and initialized.
$ git clone --recurse-submodules <repository_url>

# Lists the submodules, their current commits, and their paths in the parent repository.
$ git submodule status

# Updates the submodules to their latest commits by fetching changes from the submodule repositories.
$ git submodule update --remote

# Initializes the submodules listed in the .gitmodules file.
$ git submodule init

# Fetches the submodule contents and checks out the specific commit or branch mentioned in the parent repository.
$ git submodule update
```


[git advance topic link](https://youtu.be/qsTthZi23VE?si=vyB1BYmJjBI-9Ci0) <br>
[interaction rebase doc](https://about.gitlab.com/blog/2020/11/23/keep-git-history-clean-with-interactive-rebase/) <br>
[rewriting git history](https://www.atlassian.com/git/tutorials/rewriting-history#:~:text=You%20can%20add%20or%20remove,shared%20with%20other%20team%20members.) <br>






