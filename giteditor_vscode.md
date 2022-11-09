VS Code as Git editor
====
___


https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config

When you launch VS Code from the command line, you can pass the --wait --new-window argument to make the launch command wait until a new VS Code instance. This can be useful when you configure VS Code as your Git external editor so Git will wait until you close the launched VS Code instance.

Here are the steps to do so:

- Make sure you can run `code --help` from the command line and you get help.
  - if you do not see help, please follow these steps:
    - macOS: Select Shell Command: Install 'Code' command in path from the Command Palette.
    - Windows: Make sure you selected Add to PATH during the installation.
    - Linux: Make sure you installed Code via our new .deb or .rpm packages.

From the command line, run `git config --global core.editor "code --wait --new-window"`
Now you can run `git config --global -e` and use VS Code as editor for configuring Git.

### VS Code as Git difftool and mergetool

You can use VS Code's diff and merge capabilities even when using Git from command-line. Add the following to your Git configurations to use VS Code as the diff and merge tool:

```
[diff]
  tool = default-difftool
[difftool "default-difftool"]
  cmd = code --wait --diff $LOCAL $REMOTE
[merge]
  tool = code
[mergetool "code"]
  cmd = code --wait --merge $REMOTE $LOCAL $BASE $MERGED
```

This uses the `--diff` option that can be passed to VS Code to compare two files side by side. The merge tool will be used the next time Git discovers a merge conflict.

To summarize, here are some examples of where you can use VS Code as the editor:

`git rebase HEAD~3 -i` do interactive rebase using VS Code
`git commit` use VS Code for the commit message
`git add -p` followed by `e` for interactive add
`git difftool <commit>^ <commit>` use VS Code as the diff editor for changes
Working with GitHub Pull Requests and Issues