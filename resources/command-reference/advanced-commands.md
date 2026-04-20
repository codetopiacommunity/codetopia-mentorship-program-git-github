# Advanced Commands — Reference

Save these for Week 6 onward.

## Rewriting history

```bash
git rebase main                 # replay current branch on top of main
git rebase -i HEAD~5            # interactive: squash, reword, drop
git commit --amend --no-edit    # add staged changes to last commit
```

## Cherry-picking

```bash
git cherry-pick <commit>        # copy one commit onto current branch
git cherry-pick <a>..<b>        # copy a range (exclusive of <a>)
```

## Reflog & recovery

```bash
git reflog                       # everywhere HEAD has been
git checkout <reflog-sha>        # recover a "lost" commit
git reset --hard <reflog-sha>    # restore branch to a prior state
```

## Stash advanced

```bash
git stash push -m "WIP login"    # named stash
git stash apply stash@{2}        # apply a specific stash
git stash drop stash@{2}         # remove one
```

## Tags & releases

```bash
git tag v1.0.0                       # lightweight tag
git tag -a v1.0.0 -m "First release" # annotated tag
git push origin v1.0.0               # push the tag
```

## Bisect

```bash
git bisect start
git bisect bad                # current commit is broken
git bisect good <sha>         # this one was fine
# Git checks out a midpoint — test, then mark good/bad — repeat
git bisect reset
```

## Submodules (use sparingly)

```bash
git submodule add <url> path/
git submodule update --init --recursive
```
