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

## HEAD
1. HEAD是上次提交的指针
1. HEAD^是上上次提交
1. HEAD@{21}前21次提交
1. master@{yesterday}昨天对master提交

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

## 修改提交
1. 

1. 修改提交说明
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