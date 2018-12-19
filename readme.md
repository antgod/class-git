## ssh-key

## 多账号配置

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