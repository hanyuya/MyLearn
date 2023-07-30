## git-learn

## 常见命令命令：

### 创建git库

```
git init # 从目录创建新的git库
git init --bare #服务器端创建新的git库
```

### 设置签名

- 设置用户签名：(使用了global选项，之后在该系统上任何事，git都会使用该信息)

- 作用：区分不同开发人员的身份，这里设置的签名和登录远程库(代码托管中心)的账号、密码没有任何关系。

- 项目级别/仓库级别：仅在当前本地库范围内有效

- 信息保存位置：./.git/config 文件

  ```
  git config user.name xxx
  git config user.email xxx
  ```

- 系统用户级别：登录当前操作系统的用户范围

- 信息保存位置：~/.gitconfig 文件

  ```
  git config --global user.name xxx
  git config --global user.email xxx
  ```

- 就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名

### 查看配置列表

```
git config -l
git config --list
```

### 克隆远程仓库

```
git clone git地址
```

- 完整的把远程库下载到本地
- 创建 origin 远程地址别名
- 初始化本地库

### 创建远程库别名

```
git remote -v 查看当前所有远程地址别名
git romote add [别名] [远程地址]
```

### 状态查看

查看工作区、暂存区状态

```
git status
```

### 显示某次提交的内容

```
git show
git show $id
```

### 抛弃工作区修改

```
git checkout --<file> # 抛弃工作区修改
git checkout . # 抛弃工作区修改
```

### 删除文件

```
git rm <file> # 从版本库中删除文件
git rm <file> --cached # 从版本库中删除文件，但不删除文件
```

### 恢复文件、版本回退

#### git reset

```
git reset <file> # 从暂存区恢复到工作文件
git reset -- . # 从暂存区恢复到工作文件
git reset --hard # 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改
git reste --hard [局部索引值] # 基于索引值前进后退
git reset --hard HEAD^ # 一个^表示后退一步，n个表示后退n步
git reset --hard HEAD~n # 后退n步
```

git reset 命令三个参数

- `--soft` 参数
  - 仅仅在本地库移动HEAD指针
- `--mixed`参数
  - 在本地库移动指针HEAD指针
  - 重置暂存区
- `--hard`参数
  - 在本地库移动HEAD指针
  - 重置暂存区
  - 重置工作区

#### git revert

说明：https://blog.csdn.net/qq_36125138/article/details/118606548

- git revert是用于“反做”某一个版本，以达到撤销该版本的修改的目的。
- 比如，我们commit了三个版本（版本一、版本二、 版本三），突然发现版本二不行（如：有bug），想要撤销版本二，但又不想影响撤销版本三的提交，就可以用 git revert 命令来反做版本二，生成新的版本四，这个版本四里会保留版本三的东西，但撤销了版本二的东西。

```
git revert <$id> # 反做提交的状态，恢复动作本身也创建了一次提交对象
git revert HEAD # 恢复最后一次提交的状态
```

#### git reflog

说明：https://zhuanlan.zhihu.com/p/521722781

HEAD@{移动到当前版本需要多少步}

```
C:\leranGit>git reflog
c68355c (HEAD -> master) HEAD@{0}: reset: moving to HEAD@{1}
aea5272 HEAD@{1}: reset: moving to aea5272
c68355c (HEAD -> master) HEAD@{2}: commit: add 1.txt 2.txt
aea5272 HEAD@{3}: commit (amend): ffff
515b954 HEAD@{4}: commit: add file hello.go
f4e1820 (origin/master, origin/HEAD) HEAD@{5}: clone: from github.com:hanyuya/leranGit.git

C:\Users\why\Desktop\mygit\leranGit>git reset HEAD@{1}

C:\Users\why\Desktop\mygit\leranGit>git reflog
c68355c (HEAD -> master) HEAD@{0}: reset: moving to HEAD@{1}
aea5272 HEAD@{1}: reset: moving to aea5272
c68355c (HEAD -> master) HEAD@{2}: commit: add 1.txt 2.txt
aea5272 HEAD@{3}: commit (amend): ffff
515b954 HEAD@{4}: commit: add file hello.go
f4e1820 (origin/master, origin/HEAD) HEAD@{5}: clone: from github.com:hanyuya/leranGit.git

C:\Users\why\Desktop\mygit\leranGit>git log --oneline
c68355c (HEAD -> master) add 1.txt 2.txt
aea5272 ffff t# On branch master
f4e1820 (origin/master, origin/HEAD) test ssh
feae7f1 address modify
ced8ac4 111
9340a98 add token
24f584f merge test
41b3cd4 hot-fix
5b7d230 master test
e761775 hot-fix frist commit
903b82a third commit
457479e second commit
5ce51b3 first commit
```

### 比较文件差异

```
git diff # 不带文件名比较多个文件
git diff [文件名] # 将工作区中的文件和暂存区进行比较
git diff [本地库中历史版本] [文件名] # 将工作区中的文件和本地库历史记录比较
git diff <$id1> <$id2> # 比较两次提交之间的差异
git diff <branch1> <branch2> # 比较两个分支之间的差异
git diff --staged # 比较暂存区和版本库之间的差异
git diff --stat # 仅仅比较统计信息 查看提交记录
```

### 添加

将工作区的“新建/修改”添加到暂存区

```
git add [file name] # 将工作文件修改提交到本地暂存库
git add . # 将所有修改过的工作文件提交到暂存区
```

### 提交

将暂存区的内容提交到本地库

```
git commit -m "commit message" [file name]
-a # 跳过暂存库
-m # 直接提交信息
--amend #修改上一个提交记录
```

**场景使用**：发现前一次修改存在bug，此时可以使用amend方式追加修订。注意：前一次commit不能push到远程仓库。使用amend可以将本次修改合并到前一次修改中，且不会产生新的提交记录。

```
git add
git commit -m "上一次提交"

# 发现bug 还需要继续修改提交
# 修改代码

git add # 修改文件
git commit --amend # 修改上一次提交
```

### 推送

```
git push [别名][分支名]
```

### 拉取

```
git pull # pull = fetch + merge
git fetch [远程库地址别名][远程分支名]
git merge [远程库地址别名/远程分支名]
git pull [远程库地址别名][远程分支名]
```

解决冲突

- 如果不是基于 GitHub 远程库的最新版所做的修改，不能推送，必须先拉取。
- 拉取下来后如果进入冲突状态，则按照“分支冲突解决”操作解决即可。

### 查看历史记录

```
git log # 查看日志/历史提交信息
--oneline/--pretty=oneline # 显示简要信息
--graph # 画出树状图
-p # 显示修改
-p <file> # 显示文件修改
-p -2 # 查看最近两次详细修改内容的diff
--stat # 查看提交统计信息
-<n> # 显示日志个数限制
--<path>
--name-only # 仅在提交信息后显示已修改的文件清单
--name-status # 显示新增、修改、删除的文件清单
-Sfunction_name # 列出那些 添加或移除了某些字符串的提交
help 查看帮助
```

多屏显示控制方式：

- 空格 向下翻页
- b 向上翻页
- q 退出

`git log --oneline`

```shell
C:\leranGit>git log --oneline
f4e1820 (HEAD -> master, origin/master, origin/HEAD) test ssh
feae7f1 address modify
ced8ac4 111
9340a98 add token
24f584f merge test
41b3cd4 hot-fix
5b7d230 master test
e761775 hot-fix frist commit
903b82a third commit
457479e second commit
5ce51b3 first commit
```

### 分支管理

#### 查看分支

```
git branch -v # 查看本地所有分支
git branch -r # 查看远端分支
```

#### 创建分支

```
git branch [分支名字]
```

#### 切换分支

```
git checkout [分支名字] # 切换分支
git checkout -b [分支名字] # branch + checkout 创建分支并切换
git checkout --<path> # 放弃修改
```

#### 删除分支

```
git branch -d [分支名字] # 删除本地分支
git branch -D [分支名字] # 强制删除本地分支
```

#### 合并分支

```
git checkout [被合并分支名]
git merge [有新内容分支名]
# 解决冲突
# 冲突的解决
# 第一步：编辑文件，删除特殊符号
# 第二步：把文件修改到满意的程度，保存退出
# 第三步：git add [文件名]
# 第四步：git commit -m "日志信息"
# 注意：此时 commit 一定不能带具体文件名
```



- 设置git的文本编辑器（在windows中需要使用32为的版本）

```
git config --gloal core.editor "'C:/...' -multiInst -notabbar -nosession -noPlugin"
```

​	设置git的文本编辑器（在linux中需要使用32为的版本）

```
git config --global core.editor emacs
```

### 获取帮助

- 获取帮助

  ```
  git help <verb>
  git <verb> --help
  man git-<verb>
  ```

  可以使用-h获得更简明的参考

  ```
  git add -h
  ```

获取git仓库：

- 在已存在目录中初始化仓库（首先需要进入到需要项目的目录中（my_project））

  ```
  git init
  ```

  该命令将创建一个名为 `.git` 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件，这些文件是 Git 仓库的骨干。 但是，在这个时候，我们仅仅是做了一个初始化的操作，你的项目里的文件还没有被跟踪。

