# Git Rebase Workflow

Do this once

```
git config --global core.editor "code --wait"
git clone https://github.com/flolu/git-rebase-flow
```

## 1. Synchronize `origin/master`

```
git pull origin master
```

## 2. Write code on a feature branch

```
git checkout -b some-cool-feature
git commit -m "feat: implement awesome stuff"
git commit -m "feat: do more cool things"
git commit -m "refactor: finalize my gorgeous work"
```

## 3. Synchronize `origin/master`

```
git checkout master
git pull
```

## 4. Rebase against local `master`

```
git checkout some-cool-feature
git rebase --interactive master
```

You might need to solve some conflicts when rebasing:

```
# solve conflicting files
git add .
git rebase --continue
```

## 5. Push feature branch to remote

```
git push -u origin cool-feature
```

## 6. Create a pull requeset

Request to merge `origin/some-cool-feature` into `origin/master` with the GitHub user interface

## 7. Change pull request

Often, you want to do some changes to the open pull request. Here is how you can dot that:

```
git checkout some-cool-feature
git commit -m "fix: some additional improvements"
```

Then repeat steps 3, 4 and 5

## 8. **Admin** merges pull request

```
git fetch origin
git checkout -b some-cool-feature origin/some-cool-feature
git checkout master
git rebase some-cool-feature
git push
git push origin -d some-cool-feature
```

## 9. Clean up

```
git branch -d some-cool-feature
```
