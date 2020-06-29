# GIT 
### 初始化仓库
```bash
    git init
```
### 查看git仓库状态
```bash
    git status
```
___
```
    On branch master

    No commits yet

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            git.md
            test01.txt

    nothing added to commit but untracked files present (use "git add" to track)
```
___
### 添加到暂存区
```bash
    git add <文件名>
```
### 从暂存区移除
```bash
    git rm --cached <文件名>
    git restore --staged <文件名>
```
### 提交到仓库
```bash
    git commit (全部提交)-a
    git commit <文件名>
    git commit <文件名> -m "需要写的备注"
```
### 设置git 用户名和邮箱
```bash
    git config [ (全局)--global || (项目) --local ] user.name <名字>
    git config [ (全局)--global || (项目) --local ] user.email <邮箱>
```
### 查看git 用户名和邮箱
```bash
    git config user.name
    git config user.email
    #查看配置信息 
    git config -l
```
### 删除git 用户名和邮箱
```bash
    git config [ (全局)--global || (项目) --local ] --unset [ user.name || user.email ]
```
### 回退文件
```bash
    git checkout -- <文件名>
```
### 删除文件
```bash
    git rm <文件名>
```
### 恢复被删除的文件(未commit)
```bash
    git restore --staged <文件名> #把被删除的文件取消暂存区的操作
    git checked -- <文件名> #把被删除的文件恢复
```