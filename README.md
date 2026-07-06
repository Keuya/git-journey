# git-journey

Started as two text files while learning `git add` and `git commit`. Kept as a
living reference of the git I actually use day to day — the original practice
files live on in `practice/`.

## The daily loop

```bash
git status                  # what changed
git add -p                  # stage in reviewable chunks (not `add .` blindly)
git commit -m "verb: what and why"
git push
```

## Branching without fear

```bash
git switch -c feature-x     # new branch
git switch main             # back to main
git merge feature-x         # bring it in
git branch -d feature-x     # clean up
```

## When something goes wrong (the part worth writing down)

| Situation | Fix |
|---|---|
| Committed to the wrong branch | `git switch correct-branch && git cherry-pick <sha>`, then remove from the wrong one |
| Want to undo the last commit, keep the work | `git reset --soft HEAD~1` |
| Want to throw away uncommitted changes to one file | `git restore <file>` |
| Committed a secret | Rotate the secret first. History rewriting comes second. |
| Merge conflict panic | `git merge --abort` gets you back to safety |
| "What did I even do today?" | `git log --oneline --since=midnight` |

## Rules I learned the hard way

1. Commit messages are for the person doing `git blame` in six months — usually me.
2. Small commits beat big ones; `git add -p` makes this cheap.
3. Never force-push a shared branch. `--force-with-lease` if it's truly yours.
4. `.gitignore` before the first commit, not after `node_modules` is in history.
5. When in doubt: commit. A messy history you can clean beats lost work.
