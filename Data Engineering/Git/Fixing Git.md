---

created: <% tp.file.creation_date() %>

---
tags:: #Git #DataEngineering 


---
# Fixing Git
---

#### Description:
For when shit hits the fan. Screwing up git is often easy and this guide provides some resolution to the headache.

## Git Time machine
```bash
git reflog
# you will see a list of every thing you've
# done in git, across all branches!
# each one has an index HEAD@{index}
# find the one before you broke everything
git reset HEAD@{index}
# magic time machine
```
You can use this to get back things automatically deleted, remove things that broke the repo, recover after a bad merge, or just go back to a time where the repo was in a working state.

## Oh shit, I committed and immediately realized I need to make one small change!

```bash
# make your change
git add . # or add individual files
git commit --amend --no-edit
# now your last commit contains that change!
# WARNING: never amend public commits
```

This usually happens to me if I commit, then run tests/linters... and FML, I didn't put a space after an equals sign. You could also make the change as a new commit and then do `rebase -i` in order to squash them both together, but this is about a million times faster.

_Warning: You should never amend commits that have been pushed up to a public/shared branch! Only amend commits that only exist in your local copy or you're gonna have a bad time._

## Oh shit, I need to change the message on my last commit!

```bash
git commit --amend
# follow prompts to change the commit message
```

Stupid commit message formatting requirements.

## Oh shit, I accidentally committed something to master that should have been on a brand new branch!

```bash
# create a new branch from the current state of master
git branch some-new-branch-name
# remove the last commit from the master branch
git reset HEAD~ --hard
git checkout some-new-branch-name
# your commit lives in this branch now :)
```

Note: this doesn't work if you've already pushed the commit to a public/shared branch, and if you tried other things first, you might need to `git reset HEAD@{number-of-commits-back}` instead of `HEAD~`. Infinite sadness. Also, many many many people suggested an awesome way to make this shorter that I didn't know myself. Thank you all!

## Oh shit, I accidentally committed to the wrong branch!

```bash
# undo the last commit, but leave the changes available
git reset HEAD~ --soft
git stash
# move to the correct branch
git checkout name-of-the-correct-branch
git stash pop
git add . # or add individual files
git commit -m "your message here";
# now your changes are on the correct branch
```

A lot of people have suggested using `cherry-pick` for this situation too, so take your pick on whatever one makes the most sense to you!

```bash
git checkout name-of-the-correct-branch
# grab the last commit to master
git cherry-pick master
# delete it from master
git checkout master
git reset HEAD~ --hard
```

## Oh shit, I tried to run a diff but nothing happened?!

If you know that you made changes to files, but `diff` is empty, you probably `add`-ed your files to staging and you need to use a special flag.

```bash
git diff --staged
```

File under ¯\_(ツ)_/¯ (yes, I know this is a feature, not a bug, but it's fucking baffling and non-obvious the first time it happens to you!)

## Oh shit, I need to undo a commit from like 5 commits ago!

```bash
# find the commit you need to undo
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git revert [saved hash]
# git will create a new commit that undoes that commit
# follow prompts to edit the commit message
# or just save and commit
```

Turns out you don't have to track down and copy-paste the old file contents into the existing file in order to undo changes! If you committed a bug, you can undo the commit all in one go with `revert`.

You can also revert a single file instead of a full commit! But of course, in true git fashion, it's a completely different set of fucking commands...

## Oh shit, I need to undo my changes to a file!

```bash
# find a hash for a commit before the file was changed
git log
# use the arrow keys to scroll up and down in history
# once you've found your commit, save the hash
git checkout [saved hash] -- path/to/file
# the old version of the file will be in your index
git commit -m "Wow, you don't have to copy-paste to undo"
```

When I finally figured this out it was HUGE. HUGE. H-U-G-E. But seriously though, on what fucking planet does `checkout --` make sense as the best way to undo a file? :shakes-fist-at-linus-torvalds:

## Fuck this noise, I give up.

```bash
cd ..
sudo rm -r fucking-git-repo-dir
git clone https://some.github.url/fucking-git-repo-dir.git
cd fucking-git-repo-dir
```

Thanks to Eric V. for this one. All complaints about the use of `sudo` in this joke can be directed to him.

For real though, if your branch is sooo borked that you need to reset the state of your repo to be the same as the remote repo in a "git-approved" way, try this, but beware these are destructive and unrecoverable actions!

```bash
# get the lastest state of origin
git fetch origin
git checkout master
git reset --hard origin/master
# delete untracked files and directories
git clean -d --force
# repeat checkout/reset/clean for each borked branch
```

---
# Links
- [Source](https://ohshitgit.com/)
---