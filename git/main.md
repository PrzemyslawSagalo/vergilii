# GIT

* [git delete tags](https://devconnected.com/how-to-delete-local-and-remote-tags-on-git/)
* `git rebase -i HEAD~n`
* `git revert` - t creates a new commit that effectively reverses the changes introduced by the merge commit

## git log
* `git log --graph --pretty=oneline`
* `--no-notes`
* git log --graph --decorate --all --oneline'

## git worktree
* `git clone --bare [repo]`
* `git worktree add [path] [branch]`
* `git worktree add [path] -b [new branch] [base branch]`

## git sync with master
* `git fetch origin`
* `git rebase origin/master`

## git pull
* `git pull --rebase`
