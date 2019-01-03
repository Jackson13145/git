# git

### 一、暂存区
```js
git add
```
    
### 二、快照
```js
git commit -m 'name'
git checkout 哈希值 //用于切换到某个快照
```

### 三、撤销
```js
git revert <commit>
```

### 四、查找哪个commit代码提交引入了错误
```js
git bisect
```
#### 1、查看log日志
```js
git log --pretty=oneline //（格式:哈希值 + name）
```
#### 2、选择排查范围
```js
git bisect start [终点] [起点] // 切换到中间的commit，从而再次查看效果
```
#### 3、排查发现没问题
```js
git bisect good // 自动切换到后半段中间的commit，从而再次查看效果
```
#### 4、排查发现有问题
```js
git bisect bad // 自动切换到good~bad中间的commit，从而再次查看效果
```
#### 5、重复排查，直到git返回
```js
哈希值 is the first bad commit // 此哈希值，即为出现错误的commit
```
#### 6、查看commit，找出错误
```js
git bisect reset // 退出查错，回到最近一次的代码提交
```
### 五、rebase
#### 1、合并多个本地commit
```js
git rebase -i 哈希值
    或
git rebase -i HEAD~number

git push -f origin 分支名
```
#### 2、rebase错误恢复
```js
git reflog
git reset --hard HEAD@{number}
git push -f 分支名
```
#### 3、rebase远程
```js
git rebase origin/远程分支名
git push -f origin 本地分支名
```
#### 4、选择一个commit，合并进当前分支
```js
git cherry-pick [commit]
```
### 六、delete 远程&本地分支
```js
git branch -d <branchName>  //本地
git push origin --delete <branchName> //远程
```