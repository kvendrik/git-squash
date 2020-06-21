# git-squash

👏 Squash all commits in your current branch into one

### What is this?
The goal here is to make cleaning up your branch commits even quicker. Please note though that `git squash` is just a slightly quicker and unified way to execute these commands:

- `git squash` runs `git rebase -i --autostash your_base_branch`. `git squash` automates changing `pick` to `squash`.
- `git squash --reset` runs `git reset "$(git merge-base your_base_branch your_target_branch)"`.

Also note that there are other speedy ways of squashing commits that are build into Git itself like [Git's `--autosquash` option](https://git-scm.com/docs/git-rebase#Documentation/git-rebase.txt---autosquash) and [`git merge --squash`](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---squash).

### Help
```
Usage: git squash [--help|-h] [--backup=<branch_name>] [--backup|-b] [--reset|-r] [<base_branch>]

Arguments
  base_branch    Branch that is used to grab the base commit to squash from (default: master)

Flags
  --reset|-r     Squashes without first updating the branch. By default we use a rebase which updates the branch before squashing.
  --backup       Back up the branch before squashing to '[target_branch]-backup'. --backup accepts a backup branch name.
  --help|-h      Print this help message
```
