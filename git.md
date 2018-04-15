Git项目中的文件和文件夹被分为三类：
1. 被追踪的(tracked)
2. 忽略的(ignored)
3. 不被追踪的(untracked)

一开始的时候，所有的文件都是不被追踪的
* 删除索引以及文档库中文件，使文件由tracked变为untracked

`git rm --cached filename`
* 删除文件并把该文件在索引以及文档库中标记为删除，在commit之后真正删除：

`git rm filename`

.gitignore文件，可使用*通配符，#开头的是注释，!表示排除，示例：
```
*.txt
#设置不要忽略note.txt文件
!note.txt
#下面的设置表示忽略整个dxx目录
dxx/
#下面的设置表示忽略目录里面的内容但保留该目录
dir/**
```
<h5>Git的三个配置文件</h5>

1~3优先级从高到底 | 对应选项
-----------|----------------------
1. 文件夹中.git子文件夹内的config文件                 | 
2. 登录账号的home directory中的.gitconfig文件   |  --global
3. Git程序的安装文件夹中的etc/gitconfig文件       | --system
* 设置用户名和邮箱：

`git config [--global] user.name 'name'`

`git config [--global] user.email 'email'`

*可加--global或者--system指定配置的存储位置，如果不指定则存储在当前的文档库中。*
* 删除配置文件中设置项，使用--unset选项

`git config --unset user.name`

*可根据配置的存储位置，加入--global或--system选项

* 配置指令别名

`git config [--global|--system] alias.指令别名 '正式的指令和选项'`

`git config alias.con 'config -l'`

`git con`

* 删除指令别名：

`git config --unset alias.con`

从0创建代码库：
```
git clone git@bitbucket.org:lcofjp/xxx.git
cd miscell
echo "# My project's README" >> README.md
git add README.md
git commit -m "Initial commit"
git push -u origin master
```
从已有的代码库上传到bitbucket：

Step 1: Switch to your repository's directory
```
cd /path/to/your/repo
```
Step 2: Connect your existing repository to Bitbucket
```
git remote add origin ssh://git@bitbucket.org/lcofjp/xxx.git
git push -u origin master
```

`git init`:初始化git文档库

`git add poem.txt`: 把poem.txt准备放入文档库

`git commit -m '操作备注‘ --author='姓名 邮箱'`: 提交到文档库。

如果提交之后想修改操作备注和操作者资料，可以：`git commit --amend -m '新的操作备注' --author='新的作者信息'`

`git add`命令后面可以使用通配符*,文件目录，或者“.", 点表示当前整个的文件夹及其子文件夹。

查询每行的最后修改者：
* `git blame -L 文件名`
* `git blame -L 起始行,结束行 文件名`

`git mv`: 改变文件或者文件夹的名称：

`git mv 原文件名 新文件名`, 这个指令会更改文件名或者文件夹名，然后把它记录在Git索引，接着执行`git commit`命令即可更新到文档库

`git show HEAD`, HEAD可简写为@

`git show commit节点:文件名`: 查看特定文件的变化
#### 恢复到指定节点
`git reset 选项 commit节点标识符或标签`

选项：
 * `--soft ` 只有文档库改变，索引和磁盘文件不变
 *  `--mixed` [默认] 文档库以及索引被改变，文件不变
 * `--hard` 全部都恢复到指定节点的状态

##### 自定义节点标签
 `git tag 自定义的标签名称 commit节点标识符或标签`
##### 删除自定义标签
`git tag -d commit节点标签`
##### 查看commit节点信息 
`git log` 加 `--graph`选项：文本模式显示commit演进图， 加`--online`选项：用最简便的方式显示演进图
### 比较
*比较：指定文件名则比较指定文件，不指定文件名或使用"."则比较所有文件*
1. `git diff 文件名`: 文件与索引比较（当索引与文档库不同）或与文档库比较（当前的索引与文档库相同）
2. `git diff commit节点1 commit节点2`: 比较文档库的两个节点
3. `git diff --cached 文件名`: 索引与文档库比较
4. `git diff commit节点 文件名`: 文件与某节点比较
5. `git diff --no-index 文件1 文件2`: 两个文件比较

### 取出文档库中的代码 checkout
`git checkout commit节点标识符或标签 文件1 文件2 ...`:
在指定节点取出文件内容。如果没指定节点，则先从索引中取，如果索引中没有，则到最新的节点中去取，最新的节点没有就去老的节点找

#### 帮助：git xxx --help / git help -a
