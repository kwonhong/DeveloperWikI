#### Git Commands
``` shell
# Cherry Picking
# After vim editor comes in, switch the order of commits & delete the commits you don't want
git rebase -i origin master
```

1. Commit Amending on Remote Repository: ```git push -f origin <branch_name>```
	* Usually, use this command after “git commit —amend” command.
2. Looking at changes by specifying git commit number: ```git show <commit_number>```
3. Making new branch: ```git checkout -b <branch_name>```
4. Deleting branch: ```git branch -d <branch_name> ```
5. Deleting remote branch: ```git push origin --delete <branchName>```

#### Git Configuration
* Reference: http://githowto.com/aliases
``` shell
# Git config file is located at $HOME directory. Opening git config with vim editor
vim ~/.gitconfig

# Include Graph Alias
dag = log --graph --oneline --decorate --date=relative --all -15

# Downloading git autoComplete
# 1. Install homebrew
# 2. Run the following command
brew install git bash-completion

# 3. Put this code in bash_profile which is in HOME directory
if [ -f `brew --prefix`/etc/bash_completion ]; then
    . `brew --prefix`/etc/bash_completion
fi
```
