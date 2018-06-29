### 1、git 提交远程

``` javascript
git init // 初始化git
git remote add origin 远程url // 添加源
git branch 分支名 // 本地创建一个分支
git checkout 分支名 // 切分支
git push origin master // 提交到远程库
```

### 2、git缓存

``` javascript
git stash list // 查看缓存列表
git stash save '内容' // 缓存并标注注释
git stash apply index // 释放缓存列表
git stash drop stash@{number} // 删除指定的缓存
git stash clear // 删除所有的stash缓存
git stash show // 展示修改过的文件
git stash list // 展示缓存的列表
```

