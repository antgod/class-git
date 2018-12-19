## 多账号配置
```
ssh-keygen -t rsa -C "A@hotmail.com"
vim ~/.ssh/config
```
编辑
```
Host github
  Host github
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa

Host gitlib
  Host gitlib
  HostName gitlib.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa_ant
```

## rebase
代码合并，修改注释并且合并注释。产生的结果是分支不产生分叉。
```
git rebase origin/master
## 修改冲突
git add .
git rebase --continue
```

- You can instead skip this commit: run "git rebase --skip".
- To abort and get back to the state before "git rebase", run "git rebase --abort".

## HEAD
1. HEAD是上次提交的指针
2. HEAD^是上上次提交
3. HEAD@{21}前21次提交
4. master@{yesterday}昨天对master提交

## 查看提交
```
git show commitId | HEAD^
```

## 储藏
```
git stash
git stash save
# 查看储藏的东西
git stash list
# 从栈上删除储藏
git stash drop stash@{2}
# 应用后立即删除
git stash pop
```

## reset 
工作区(Working directory：checkout) -> 缓存区(Index：git add) -> 提交区(Head:git commit) 

1. hard：重设index和working directory，从<commit>以来在working directory中的任何改变都被丢弃，并把HEAD指向<commit>：回到到上次提交。

1. soft: index和working directory中的内容不作任何改变，仅仅把HEAD指向<commit>。自从<commit>以来的所有改变都会显示在git status的“Changes to be committed”中。
	```
	## 回到git add之后的状态。
	git reset --soft HEAD^
	```
1. mixed：仅重设index，但是不重设working directory。这个模式是默认模式，即当不显示告知git reset模式时，会使用mixed模式。这个模式的效果是，working directory中文件的修改都会被保留，不会丢弃，但是也不会被标记成“Changes to be committed”，但是会打出什么还未被更新的报告
	```
	## 回到git add之前的状态。
	git reset --mixed HEAD^
	```

## 修改提交
1. 回到某个版本
	```
	git reset --hard commitId | HEAD^
	```

2. 修改提交说明
	```
	git commit --amend -m "xxx"
	```

## 回滚:针对已经提交
1. 回滚上次提交
	```
	git revert HEAD
	git push origin master
	```

1. 回滚多次提交
	```
	git reset --hard HEAD^
	git push origin branch -f
	```
## 拉取远程分支
```
git checkout origin/branch
```
