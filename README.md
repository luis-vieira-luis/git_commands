Git Commands
============

___

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git add .` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git commit --amend -m "[commit message]"` | Commit changes on the same commit with new message |
| `git commit --amend --no-edit` | Commit changes on the same commit with no message |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Multitask

| Command | Description |
| ------- | ----------- |
| `git stash` | “stashing” your local work temporarily in order to update a previous commit and later on retrieve your work |
| `git stash pop` | retrieve from your stash |


### Reset

| Command | Description |
| ------- | ----------- |
| `git checkout HEAD [filename]` | Discards changes in the working directory |
| `git reset HEAD [filename]` | Unstages file changes in the staging area |
| `git reset [commit_SHA]` | Resets to a previous commit in your commit history |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git show HEAD ` | Display everything the git log command displays for the HEAD commit, plus all the file changes that were committed |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git log --oneline` | View changes (briefly) |
| `git log --oneline --graph` | View branches and commits created in order to help you make sense of repository history. |
| `git log -S "keyword"` | Displays a list of commits that contain the keyword in the message. |
| `git diff [source branch] [target branch]` | Preview changes before merging |


____
### Git Alias
| Command | Description |
| ------- | ----------- |
| `git config --global alias.[command_shortcut] "command with the git part"` | Define personal shortcut commands |


___
### Clone repo
 > `git push -U origin main`


if **"remote: Support for password authentication was removed"** error occurs:

>Username for 'https://github.com': <username>
Password for 'https://your-username@github.com':
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/<username>/repo-name.git/'


#### Step 1: Create Access Token on GitHub
First of all, you must create a personal Access Token on GitHub. To do so follow the steps below:

- Click on your GitHub profile icon on the top right corner
- Click Settings
- From the menu shown on the left, click Developer Settings
- Click Personal access tokens
- Click Generate new token
- Add a note that will help you identify the scope of the access token to be generated
- Choose the Expiration period from the drop down menu (Ideally you should avoid choosing the No Expiration option)
- Finally, select the scopes you want to grant the corresponding access to the generated access token. Make sure to select the minimum required scopes otherwise you will still have troubles performing certain Git Operations.
- Finally click Generate Token

By now, you should have generated your personal access token successfully and the following message should be visible on your screen.


Source: Author
Underneath that message, you should also be able to see your personal access token. Make sure to copy it as we will need it in the following step(s).

#### Step 2: Change the remote URL
Now that we have created our personal access token, we need to run the following command:

> git remote set-url origin https://githubtoken@github.com/username/repositoryname.git

In the above command make sure to replace:
- `githubtoken` with the personal access token you have copied in the previous step
- `username` with your GitHub username
- `repositoryname` with the name of your GitHub repository


#### Step 3: Test that it works
Now we have successfully configured token-based authentication for a specific repository on GitHub. To test that everything went to plan, simply try to push the changes you’ve made locally to the remote host. For example,

> `git push -u origin main`

and the Git operation should be executed with no issues.