# Git Cheat Sheet

Scannable reference. Every command has a one-line purpose so you can find it fast.

> Git version this was written against: **2.43**

---

## Your Two Errors This Session

Worth reading first, because both are common.

```bash
# ❌  WRONG — space between - and m
git commit - m " Initial Notes"
error: pathspec '-' did not match any file(s) known to git
#          ^^^^ git read "- m" and the text as filenames

# ✅  RIGHT — no space, and no leading space in the message
git commit -m "Initial Notes"
```

```bash
# ⚠️  " Initial Notes" had a leading space, so it committed as
#     " Initial Notes" not "Initial Notes". Cosmetic, but it shows
#     up in every log. Amend it with:
git commit --amend -m "Initial Notes"
```

```bash
# ⚠️  The "master" hint on git init is noise. Silence it once, globally:
git config --global init.defaultBranch main
```

---

## The Everyday Loop

This is 95% of what you need.

```bash
git status              # what's changed? (run this first, always)
git add <file>          # stage a change
git add .               # stage everything
git add -p              # stage hunk by hunk (pick what goes in)
git commit -m "msg"     # commit
git push                # publish
```

```bash
# The full cycle
git add .
git commit -m "Fix login redirect"
git push
```

---

## Setup & Config

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main     # new repos start on main
git config --global pull.rebase true           # avoid merge commits on pull
git config --list                               # show all config
```

---

## Init & Clone

```bash
git init                        # make a new repo here
git init --initial-branch=main   # new repo, already on main
git clone <url>                 # copy a remote repo
git clone <url> <dir>           # ...into a named folder
```

---

## Staging & Committing

```bash
git add <file>                  # stage one file
git add .                       # stage all changes in this folder
git add -p                      # interactively pick hunks to stage
git add -u                      # stage tracked files only (no new files)

git commit -m "message"         # commit staged changes
git commit -am "message"        # stage tracked + commit in one go
git commit --amend -m "new"     # rewrite the LAST commit's message
git commit --amend --no-edit    # add forgotten changes to last commit
```

### Unstage

```bash
git restore --staged <file>     # unstage, keep the change
git reset HEAD <file>           # same thing, older syntax
```

---

## Branching

```bash
git branch                      # list local branches
git branch -a                   # list local + remote
git branch -v                   # with last commit message
git branch -d <branch>          # delete a merged branch
git branch -D <branch>          # delete regardless (careful)

git switch <branch>             # move to a branch  ✅ use this
git switch -c <branch>          # create AND move to it
git checkout <branch>           # older equivalent of switch
git checkout -b <branch>        # older equivalent of switch -c

git merge <branch>              # merge branch into current
git merge --no-ff <branch>      # force a merge commit, keep history
```

### Renaming / tracking

```bash
git branch -M main              # rename current branch (you used this ✅)
git push -u origin main         # push + set upstream (you used this ✅)
```

---

## Remotes

```bash
git remote add origin <url>     # add a remote      (you used this ✅)
git remote -v                   # list remotes      (you used this ✅)
git remote set-url origin <url> # change the URL
git remote remove origin        # drop a remote

git fetch origin                # download, don't merge
git pull                        # fetch + merge into current branch
git push                        # publish current branch
git push -u origin <branch>     # first push of a new branch
git push --force-with-lease     # force push, but safer than --force
```

**`fetch` vs `pull`:** `fetch` is safe — it only downloads. `pull` fetches
*and* changes your working tree. When in doubt, `fetch`.

---

## Inspecting

```bash
git status                      # current state
git status -sb                  # short + branch
git log                         # full history
git log --oneline                # one line per commit
git log --oneline --graph --all # pretty tree, all branches
git log -p <file>                # history of one file, with diffs
git show <sha>                  # details of one commit
git diff                        # unstaged changes
git diff --staged               # staged changes
git blame <file>                # who changed each line
```

---

## Undo & Recovery

**The one people panic about.** Work top-to-bottom — the first one that applies is the one you want.

```bash
# Unstage, keep changes
git restore --staged <file>

# Rewrite the last commit, keeping the changes staged
git reset --soft HEAD~1

# Same, but unstage them too (default mode)
git reset HEAD~1

# ⚠️ DANGER — discard the last commit AND its changes
git reset --hard HEAD~1

# ✅ Safest for shared history: a new commit that undoes an old one
git revert <sha>

# Staged a secret or a huge file? Remove from the index, keep on disk
git rm --cached <file>
```

```bash
# ✅ The "I destroyed everything" escape hatch — ALWAYS try this first
git reflog
# shows every position HEAD has been at, including ones you thought you lost
git reset --hard <sha-from-reflog>
```

| Mode | Moves HEAD | Keeps changes | Keeps them staged |
|---|---|---|---|
| `--soft` | yes | yes | yes |
| `--mixed` (default) | yes | yes | no |
| `--hard` | yes | **no** | no |

---

## Stash (park work-in-progress)

```bash
git stash                      # save current changes, clean the tree
git stash -u                   # also stash untracked files
git stash list                 # see what's parked
git stash show -p              # view the most recent stash
git stash pop                  # restore AND delete the stash
git stash apply                # restore but KEEP the stash
git stash drop                 # delete a stash without restoring
git stash clear                # delete all stashes
```

---

## Temporary Commits

```bash
git commit -m "WIP"    # quick marker commit
git commit --fixup <sha>   # marked as a fix for a specific commit
```

---

## Useful Aliases

```bash
git config --global alias.st "status -sb"
git config --global alias.lg "log --oneline --graph --all --decorate"
git config --global alias.last "log -1 HEAD --stat"
git config --global alias.unstage "restore --staged"
git config --global alias.amend "commit --amend --no-edit"
```

---

## Stashing vs Branching

Both "save work and switch tasks" — different intent:

```bash
git switch -c feature-x    # NEW BRANCH — work belongs to a separate line of history
                            # ✅ for features, experiments, anything you'll merge

git stash                  # STASH — work is temporary and not a real line of history
                            # ✅ for "I need to check something else for 5 minutes"
```

---

## Recovering From Common Mistakes

| Symptom | Fix |
|---|---|
| Wrong commit message | `git commit --amend -m "correct message"` |
| Forgot a file in the commit | `git add <file> && git commit --amend --no-edit` |
| Committed secrets | `git rm --cached <file>` then rotate the secret **now** |
| Wrong branch committed to | `git reset --soft HEAD~1 && git switch -c correct-branch` |
| Push rejected (non-fast-forward) | `git fetch origin && git rebase origin/main` (then resolve and re-push) |
| Pushed something you shouldn't have | `git revert` it — never force-push shared history |
| Merge conflict | Fix the files, then `git add <files> && git commit` |
| Want to abort a merge | `git merge --abort` |
| Want to check out a previous commit | `git switch --detach <sha>` (read-only) |
| Deleted a file by accident | `git restore <file>` (before committing) |

---

## A Few Rules That Save Pain

1. **Commit often.** Small commits are easy to revert; one giant commit is not.
2. **Write the message for your future self.** `git log` is a to-do list, not a diary.
3. **Never `--force` push shared branches.** Use `--force-with-lease` if you must.
4. **Never `--hard reset` to "try something".** `git stash` is the safe version.
5. **Check `git status` before committing.** It catches the accidentally-added file.
6. **`git reflog` is your undo button.** Nothing is truly lost until it's garbage collected.
7. **`.gitignore` first**, in a new repo, before the first `git add .`

---

## Cheat Sheet Card

```bash
# setup
git config --global user.name "Name"
git config --global user.email "email"
git config --global init.defaultBranch main

# daily
git status · git add . · git commit -m "msg" · git push

# branch
git switch -c <new> · git switch <old> · git merge <branch>

# remote
git clone <url> · git remote -v · git pull · git push -u origin <branch>

# inspect
git log --oneline --graph --all · git diff · git show <sha>

# undo
git restore --staged <file>      # unstage
git reset --soft HEAD~1          # undo last commit, keep changes
git revert <sha>                 # safe undo of shared commit
git reflog                       # rescue anything
```

Related: [../python_notes/common/Common_Patterns.md](../python_notes/common/Common_Patterns.md)
