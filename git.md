### 1、项目提交远程

``` javascript
git init // 初始化git
git remote add origin 远程url // 添加源
git branch 分支名 // 本地创建一个分支
git checkout 分支名 // 切分支
git push origin master // 提交到远程库
git push -u origin master // git第一次提交
git push -u origin master -f // git强制提交到远程
```

### 2、git stash  缓存

``` javascript
git stash save '内容' // 缓存并标注注释
git stash show // 展示修改过的文件
git stash list // 查看缓存列表
git stash apply index // 释放缓存列表
git stash drop stash@{number} // 删除指定的缓存
git stash clear // 删除所有的stash缓存
git stash list // 展示缓存的列表
```

## 3、git clone 

``` javascript
git clone <版本库的网址>  // 从远程克隆一个版本库(支持多协议)
```

## 4、git remote

``` javascript
git remote // 列出所以远程主机
git remote -v // 查看远程主机的网址
git remote show <主机名> // 查看源<查看主机的详细信息>
git remote add <主机名> // 添加远程主机
git remote rm <主机名> // 删除远程主机
git remote rename <原主机名> <新主机名> // 远程主机改名
```

## 5、git fetch

``` javascript
git fetch <远程主机名> <分支名> // 取回所有分支(branch)的更新(指定分支名)
git branch -r // -r 查看远程分支  -a选项查看所有分支
git checkout -b feature-B origin/master // 在master的基础上创建一个新分支
git merge 和 git rebase // 在本地分支上合并远程分支
```

## 6、git pull

``` javascript
git pull <远程主机> <远程分支名>:<本地分支名> // 取回远程主机某个分支 和本地的指定分支合并
// 例 git pull origin master:master 简为 git pull origin master 简为 git pull origin 简为 git pull
// 分解 git fetch origin  +   git merge origin/master
git pull --rebase <远程主机名> <远程分支名>:<本地分支名> // rebase选项

```

## 7、git push

``` javascript
git push <远程主机> <本地分支名>:<远程分支名>
git push origin master:master|git push origin :master|git push origin|git push
git push -u origin master （-f）// 第一次提交的时候(强制提交的时候)
git push --all origin // 将所有的本地分支都推到远程主机
git push --force origin // 强制推送远程(尽量避免使用)
git push origin --tags // 打tages标签
```

## 8、git tag（标注版本打tag）

``` javascript
git tag // 查看版本
git tag 标签名 // 为历史版本打标签
git tag 标签名 该版本ID // 为历史版本打标签
git tag -a 标签名 -m '标签说明' [可选：版本ID] // 创建版本(指定标签打tag)
git tag -d 标签名 // 删除版本
git tag -r // 查看远程版本
git show 标签名 // 查看某一标签

```

## 9、回退版本撤销

``` javascript
// HEAD: 当前版本  HEAD^: 上一个版本 --hard: 参数会抛弃当前工作区的修改  --soft: 参数的话会回退到之前版
git reset HEAD . // 撤销所有add文件  add撤销
git reset HEAD -filename // 撤销单个add文件

git reset --soft head // 只回退commit信息   commit撤销
git reset --hard head^ // 彻底回退到上次commit版本，不保留修改代码

git log 查看commit信息 // git push 撤销
git revert 以前commit的id
git push 此时本地回滚的代码到服务器 // over

git checkout [merge操作时所在的分支] // git merge 撤销
git reset --hard [merge前的版本号] // over
  
git checkout . // 撤销所有本地改动代码 
git reset --hard 远程仓库名 // 本地代码回退到与git远程仓库一致

git reset --hard HEAD/commit_id // 回滚到历史版本
git reset --hard HEAD^ // 回退到上个版本(HEAD^^ 上上版本)
```

## 10、查询有关

``` javascript
git status // 查询创库状态
git diff 文件名 // 比较文件差异(在git add之前使用)
git log // 查看仓库历史记录(详细)
git reflog // 查看所有版本的commit ID
```











## Git 命令详解

现在我们有了本地和远程的版本库，让我们来试着用用Git的基本命令：

**git pull：**从其他的版本库（既可以是远程的也可以是本地的）将代码更新到本地，例如：'git pull origin master'就是将origin这个版本库的代码更新到本地的master主枝，该功能类似于SVN的**update**

**git add：**是将当前更改或者新增的文件加入到Git的索引中，加入到Git的索引中就表示记入了版本历史中，这也是提交之前所需要执行的一步，例如'git add app/model/user.rb'就会增加app/model/user.rb文件到Git的索引中，该功能类似于SVN的**add**

**git rm：**从当前的工作空间中和索引中删除文件，例如'git rm app/model/user.rb'，该功能类似于SVN的**rm、del**

**git commit：**提交当前工作空间的修改内容，类似于SVN的commit命令，例如'git commit -m story #3, add user model'，提交的时候必须用-m来输入一条提交信息，该功能类似于SVN的**commit**

**git push：**将本地commit的代码更新到远程版本库中，例如'git push origin'就会将本地的代码更新到名为orgin的远程版本库中

**git log：**查看历史日志，该功能类似于SVN的**log**

**git revert：**还原一个版本的修改，必须提供一个具体的Git版本号，例如'git revert bbaf6fb5060b4875b18ff9ff637ce118256d6f20'，Git的版本号都是生成的一个哈希值

上面的命令几乎都是每个版本控制工具所公有的，下面就开始尝试一下Git独有的一些命令：

**git branch：**对分支的增、删、查等操作，例如'git branch new_branch'会从当前的工作版本创建一个叫做new_branch的新分支，'git branch -D new_branch'就会强制删除叫做new_branch的分支，'git branch'就会列出本地所有的分支

**git checkout：**Git的checkout有两个作用，其一是在不同的branch之间进行切换，例如'git checkout new_branch'就会切换到new_branch的分支上去；另一个功能是还原代码的作用，例如'git checkout app/model/user.rb'就会将user.rb文件从上一个已提交的版本中更新回来，未提交的内容全部会回滚

**git rebase：**用下面两幅图解释会比较清楚一些，rebase命令执行后，实际上是将分支点从C移到了G，这样分支也就具有了从C到G的功能

**git reset：**将当前的工作目录完全回滚到指定的版本号，假设如下图，我们有A-G五次提交的版本，其中C的版本号是 bbaf6fb5060b4875b18ff9ff637ce118256d6f20，我们执行了'git reset bbaf6fb5060b4875b18ff9ff637ce118256d6f20'那么结果就只剩下了A-C三个提交的版本

** **

**git stash：**将当前未提交的工作存入Git工作栈中，时机成熟的时候再应用回来，这里暂时提一下这个命令的用法，后面在技巧篇会重点讲解

**git config：**利用这个命令可以新增、更改Git的各种设置，例如'git config branch.master.remote origin'就将master的远程版本库设置为别名叫做origin版本库，后面在技巧篇会利用这个命令个性化设置你的Git，为你打造独一无二的 Git

**git tag：**可以将某个具体的版本打上一个标签，这样你就不需要记忆复杂的版本号哈希值了，例如你可以使用'git tag revert_version bbaf6fb5060b4875b18ff9ff637ce118256d6f20'来标记这个被你还原的版本，那么以后你想查看该版本时，就可以使用 revert_version标签名，而不是哈希值了

Git 之所以能够提供方便的本地分支等特性，是与它的文件存储机制有关的。Git存储版本控制信息时使用它自己定义的一套文件系统存储机制，在代码根目录下有一个.git文件夹，会有如下这样的目录结构：



有几个比较重要的文件和目录需要解释一下：HEAD文件存放根节点的信息，其实目录结构就表示一个树型结构，Git采用这种树形结构来存储版本信息，那么HEAD就表示根；refs目录存储了你在当前版本控制目录下的各种不同引用（引用指的是你本地和远程所用到的各个树分支的信息），它有heads、remotes、stash、tags四个子目录，分别存储对不同的根、远程版本库、Git栈和标签的四种引用，你可以通过命令'git show-ref'更清晰地查看引用信息；logs目录根据不同的引用存储了日志信息。因此，Git只需要代码根目录下的这一个.git目录就可以记录完整的版本控制信息，而不是像SVN那样根目录和子目录下都有.svn目录。那么下面就来看一下Git与SVN的区别吧

















