
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
- To start working in a different branch, use git checkout to switch branches.
```
# Checkout an existing branch
$ git checkout <branch_name>

# Checkout and create a new branch with that name
$ git checkout -b <new_branch>

# Rename a local branch
$ git branch -m [old branch name] [new branch name]
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
```

```
# To display the first 10 commits 
$ git log -10
```


**git reset**
- Git reset is a command that moves the current head of the branch back to a specified commit. This can be used to `undo commits that have not been pushed to a remote repository`.

<hr>

**git rm**
- Remove files or directories from the working index (staging area). With git rm, there are two options to keep in mind: force and cached. Running the command with force deletes the file. The cached command removes the file from the working index. When removing an entire directory, a recursive command is necessary.
```
# To remove a file from the working index (cached):
$ git rm --cached <file name>

# To delete a file (force):
$ git rm -f <file name>

# To remove an entire directory from the working index (cached):
$ git rm -r --cached <directory name>

# To delete an entire directory (force):
$ git rm -r -f <file name>
```

**Temporarily switch to a different commit**
- If you want to temporarily go back to it, fool around, then come back to where you are, all you have to do is check out the desired commit:
```
# This will detach your HEAD, that is, leave you with no branch checked out:
git checkout 0d1d7fc32
```

- To go back to where you were, just check out the branch you were on again. (If you've made changes, as always when switching branches, you'll have to deal with them as appropriate. You could reset to throw them away; you could stash, checkout, stash pop to take them with you; you could commit them to a branch there if you want a branch there.)
```
git checkout -b old-state 0d1d7fc32
```

**Hard delete unpublished commits**
- If, on the other hand, you want to really get rid of everything you've done since then, there are two possibilities. One, if you haven't published any of these commits, simply reset:
```
# This will destroy any local modifications.
# Don't do it if you have uncommitted work you want to keep.
git reset --hard 0d1d7fc32

#To change the above hard reset to remote
git push -f origin master

# Alternatively, if there's work to keep:
git stash
git reset --hard 0d1d7fc32
git stash pop
# This saves the modifications, then reapplies that patch after resetting.
# You could get merge conflicts, if you've modified things which were
# changed since the commit you reset to.
```




