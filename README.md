# git-squash

👏 Squash all commits in your current branch into one

![](demo.gif)

## Installation
```
brew install kvendrik/osx/git-squash
```

## Example
```
git log
* 834c8e6 - (HEAD -> new-feature) Sets up build script (3 seconds ago) <Koen Vendrik>
* 590c3a5 - Sets up CI (5 seconds ago) <Koen Vendrik>
* 2b44299 - (master) adds template (42 minutes ago) <Koen Vendrik>

git squash "Sets up tooling"
[detached HEAD ea22831] Sets up tooling
 Date: Sun Jun 21 14:52:18 2020 -0400
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 .ci.yml
 create mode 100644 build.sh
Successfully rebased and updated refs/heads/new-feature.

git log
* ea22831 - (HEAD -> new-feature) Sets up tooling (12 seconds ago) <Koen Vendrik>
* 2b44299 - (master) adds template (42 minutes ago) <Koen Vendrik>
```

## What this does

The goal here is to make cleaning up your branch commits even quicker. Please note though that `git squash` is just a slightly quicker and unified way to execute these commands:

- `git squash` runs `git rebase -i --autostash your_base_branch`. `git squash` automates changing `pick` to `squash` and inserts your commit message so this workflow is reduced to a single command.
- `git squash --reset` runs `git reset "$(git merge-base your_base_branch your_target_branch)"`.

Also note that there are other speedy ways of squashing commits that are build into Git itself like [Git's `--autosquash` option](https://git-scm.com/docs/git-rebase#Documentation/git-rebase.txt---autosquash) (which provides more control over what you're squashing) and [`git merge --squash`](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---squash) (which lets you automatically squash all commits together and merge).

## Help

```
Usage: git squash [--help|-h] [--backup=<branch_name>] [--backup|-b] [--reset|-r] [--base=<base_branch>] <commit_message>

Arguments
  commit_message    The commit message to use when commiting the squashed commit

Flags
  --base            Branch that you eventually intend on merging into (default: master)
  --backup|-b       Back up the branch before squashing to '[target_branch]-backup'. --backup accepts a backup branch name.
  --reset|-r        Squashes without first updating the branch. By default we use a rebase which updates the branch before squashing.
  --help|-h         Print this help message
```
