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
    git add . (把当前文件夹和子文件夹的所有文件都加入暂存区)
```
### 从暂存区移除
```bash
    git rm --cached <文件名>
    git restore --staged <文件名>
```
### 提交到仓库
```bash
    git commit (强制提交)-a
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
    git restore --staged <文件名> #把被删除的文件 暂存区的操作 恢复到工作区
    git checkout -- <文件名> #把被删除的文件恢复
```
### git 修改文件名字
```bash
    git mv <旧文件名> <新文件名>
```
### 修改提交的日志message
```bash
    git commit --amend -m 'XXX'
```
### 查看提交日志
```bash
    git log [-3]#可选: -N 显示N条
    git log --pretty=oneline #只显示commitID 和message
    git log --pretty=format:"%h - %an,%ar : %s" #只显示commitID 和message
```
___
```
    7ad84d4 - xiaokedamowang,36 minutes ago : 重新写message
    160e4aa - xiaokedamowang,39 minutes ago : 提交md
    c561b4c - xiaokedamowang,41 minutes ago : 删除测试
    a9a654a - xiaokedamowang,69 minutes ago : aaa啊啊啊
    99d5b95 - xiaokedamowang,85 minutes ago : 第三次提交
    61d7afe - xiaokedamowang,86 minutes ago : di er ci tijiao
    0cbec06 - xiaokedamowang,88 minutes ago : di er ci tijiao
    90dd778 - xiaokedamowanmg,2 hours ago : di yi ci tijiao
    cdfcdd2 - xiaokedamowanmg,2 hours ago : 第一次提交

```
___
### git 忽略某些文件不提示未加入仓库
创建名为: .gitignore 的文件
在里面写上需要忽略的文件名 或者文件夹名
```bash
    # 这样会忽略motest.txt 和target 文件夹  
    notest.txt
    target/
    # .xml结尾的也会忽略,但是aaa.xml不会
    *.xml
    !aaa.xml
    # 子目录下的aa.txt忽略
    /*/aa.txt 
    # 所有目录下的aa.txt 都忽略
    /**/aa.txt 
```
### 查看分支
```bash
    git branch
```
### 创建分支
```bash
    git branch <分支名字>
```
### 切换分支
```bash
    git checkout <分支名字>
```

