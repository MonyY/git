# Git 常用命令

```sh
git ls-files # 查看被追踪的文件
git (checkout || restore) <./文件名> # 删除全部/文件中未commit的修改
git (checkout -b || switch -c) <分支名> # 创建并切换至分支
git clean -dn # 查看哪些未add的文件会被删除
git clean -df # 删除所有未add的文件
git restore --staged <文件名> # 将已add但未commit的文件撤回到未add的状态
```
