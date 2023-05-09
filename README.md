# Git 常用命令

```sh
git ls-files # 查看被追踪的文件
git (checkout || restore) <./文件名> # 删除全部/文件中未commit的修改
git (checkout -b || switch -c) <分支名> # 创建并切换至分支
git checkout  <commitID> # 切换至对应commit，处于分离头状态
git clean -dn # 查看哪些未add的文件会被删除
git clean -df # 删除所有未add的文件
git restore --staged <文件名> # 将已add但未commit的文件撤回到未add的状态
# --soft: 撤回commit，但保留add状态，可直接再次commit
# --hard: 撤回所有，新文件会被删除
# --mixed（默认）: 撤回commit，不保留add状态
git reset --soft (commitID || HEAD~1) # 回退commit
git stash push -m '备注' # 将当前未commit的修改缓存
git stash apply # 恢复到最新的缓存，但保留缓存
git stash pop # 恢复到最新的缓存，删除缓存
git stash clear # 删除所有缓存
git reflog # 查看30天内的git操作记录
git merge --squash <分支名> # 将其它分支的所有commit合并到当前分支的工作区，避免在当前分支添加新分支的commit记录，在当前分支统一commit
git tag <标签名> <commitID> # 给特定commit添加tag
git tag -d <tag> # 删除指定tag
git show <标签名> # 通过tag查看commit
git commit --amend -m '备注' # 覆盖上一次commit
git push -u origin master # -u: 将当前分支与远端master对应，以后就可以直接git push
git push origin --delete <分支名> # 删除远程分支
```

# Git 常用组合

1. 在之前某次 commit 追加提交。

```sh
git checkout <commitID> # 切换至对应commit，添加修改并commit
git branch <新分支名> (<detached-id> || <tag>)# 基于分离头id创建新分支
git switch <分支名> # 切换到主分支
git merge <新分支名> # 将基于分离头id创建的新分支合并到当前分支
```

2. 在当前分支修复了其它分支的一个问题，只将修复问题的 commit 合并到其它分支

```sh
git commit  # 修复问题前先commit手头内容
git commit  # commit修复其它分支的代码
git log  # 获取修复代码的commitID
git switch <分支名> # 切换到需要修复的分支
git cherry-pick <commitID> # merge修复代码的commitID
```

3. 贡献开源库代码

```sh
fork开源库代码到自己仓库
git clone <forked仓库>
git switch -c <分支名> # 在自己的功能分支开发
git add && commit && push  # 常规提交代码
git remote add upstrem <fork仓库地址> # 新建一个名为upstrem的仓库，指向fork
git switch <分支名> # 切换到要同步的分支
git pull --rebase upstrem <分支名> # 从仓库分支拉取代码
```
