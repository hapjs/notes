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
```

### merge

合并，即创建一个新的提交，同时指向两个分支（当前分支和指定分支）
```
git merge master
```
