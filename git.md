# git 知识

整理了git常用命令

### branch

创建分支
```
git branch bugFix
```

### checkout

切换到分支
```
git checkout bugFix
```

### rebase 

让当前分支移动到指定分支之后（包含指定分支的所有提交）
```
git rebase master
git rebase HEAD^
git rebase HEAD~4
git rebase -i HEAD~4
```

### merge

合并，即创建一个新的提交，同时指向两个分支（当前分支和指定分支）
```
git merge master
```

### reset

回退
```
git reset HEAD^
git reset HEAD~4
git reset C1
```

### revert

回退（会产生一个新的提交）
```
git revert HEAD^
git revert HEAD~4
git revert C1
```

### cherry-pick

复制指定的提交到当前分支
```
git cherry-pick C1 C2 C5
```
