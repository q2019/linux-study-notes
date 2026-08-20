#

## 1. 查看当前所在分支

```bash
git branch
```

或

```bash
git status
```

## 2. 查看远程仓库的默认分支（HEAD 指向）

```bash
git remote show origin
```

HEAD branch 表示 HEAD 指向的分支

Remote branches 表示所有分支

如下表示，远程仓库有5个分支，HEAD 指向 master 分支

```bash
  HEAD branch: master
  Remote branches:
    develop tracked
    feature tracked
    hotfix  tracked
    master  tracked
    release tracked
```

## 3.查看所有本地分支及其上游跟踪分支

```bash
git branch -a
git branch --all
```

返回

```bash
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/feature
  remotes/origin/hotfix
  remotes/origin/master
  remotes/origin/release
```

## 999. 其他

```bash
# 显示详细内容
git branch -v
git branch --verbose
# 显示更详细内容
git branch -vv

```

返回

```bash
# git branch -v 返回
* master 58b239e [ahead 1]      modified:   README.md
# git branch --verbose 返回
* master 58b239e [ahead 1]      modified:   README.md
# git branch -vv 返回
* master 58b239e [origin/master: ahead 1]       modified:   README.md
```

1.本地与远程同步后，本地提交 commit 一次之后，还没有同步到远程地址，本地比远程超前，显示 ahead 1.
2.本地再次修改文件，再次提交 commit 一次之后，还没有同步到远程地址，本地比远程超前，显示 ahead 2.
3.本地再次修改文件，此时选择提交修改 commit 一次之后，还没有同步到远程地址，本地比远程超前，显示 ahead 2.

```bash
git commit --amend -m 'test'
```

## 4. 切换到其他分支

```bash
git checkout <分支名>
```

```bash
$ git checkout 
develop   FETCH_HEAD   hotfix   ORIG_HEAD   origin/feature  origin/hotfix   origin/release
feature   HEAD   master   origin/develop   origin/HEAD   origin/master   release
```

按下tab键，会提示有多个分支，区别如下：

全小写的为 `本地分支`
位置：存在于本地 .git/refs/heads/ 目录下.
含义：本地分支，你可以在本地切换、修改、提交.
操作：可以直接 git checkout feature 切换过去.

```bash
develop    feature    hotfix    master    release
```

origin/xxx 为（远程跟踪分支）
位置：存在于本地 .git/refs/remotes/origin/ 目录下.
含义：远程分支的本地镜像，表示最后一次 git fetch 时远程仓库的状态.
操作：可以 git checkout origin/feature，但会进入 detached HEAD 状态（不在任何分支上，只是查看）.
注意：这些不是真正的本地分支，只是只读的指针.

```bash
origin/develop    origin/feature    origin/HEAD    origin/hotfix    origin/master    origin/release
```

全大写名称（Git 内部文件）

```bash
FETCH_HEAD    HEAD    ORIG_HEAD
```

```bash
# 切换到 develop 分支
git checkout develop

# 切换到 feature 分支
git checkout feature

# 切换到 hotfix 分支
git checkout hotfix

# 切换到 release 分支
git checkout release
```

## 工作区 暂存区 本地仓库 之间的关系

修改文件：你在 README.md 里加了一行字。

文件状态：工作区 (Modified)

Git 状态：git status 显示红色 modified: README.md

暂存更改

```bash
git add README.md
```

取消暂存更改

```bash
git restore --staged README.md
```

文件状态：暂存区 (Staged)

Git 状态：git status 显示绿色 modified: README.md

提交到仓库：执行 git commit -m "更新说明"

文件状态：本地仓库 (Committed)，暂存区被清空

Git 状态：git status 显示 nothing to commit, working tree clean

## 查看本地所有提交的历史，并回退到某一提交

命令

```bash
git log --oneline
```

返回（绿色的分支名表示是本地有该分支，红色的是远程分支）

```bash
$ git log --oneline
4fb72f7 (HEAD -> master, origin/master, origin/HEAD)    modified:   README.md
70f465d         modified:   README.md
f387675         modified:   README.md
f0ac2a5         modified:   README.md
2f47681         modified:   README.md
58b239e         modified:   README.md
5c900ba (origin/release, origin/hotfix, origin/feature, origin/develop, hotfix) Initial commit
```

回退到指定分支 git reset --hard

```bash
$ git reset --hard f0ac2a5
HEAD is now at f0ac2a5  modified:   README.md
```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```
