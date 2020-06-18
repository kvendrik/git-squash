# [WIP] git-squash

![](git-squash-demo.gif)

```
Usage: git squash [<base_branch>] [<target_branch>] [<backup_branch>]

base_branch    Branch that is used to grab the base commit to squash from (default: master)
target_branch  Branch to squash commits on (default: branch you're currently on)
backup_branch  Name of branch that will be created as a backup of target_branch before squashing (default: target_branch suffixed with "-backup")
```
