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
    git reset HEAD <文件名>
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
    # git reset HEAD <文件名>  该命令也可以
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
    git log --graph #图形化显示
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
    git branch <分支名字> <commitId> # 创建分支 基于某次提交
```
### 切换分支
```bash
    git checkout <分支名字>
```
### 删除分支
```bash
    git branch -d <分支名字>
    # 如果要删除没有被合并的分支
    git branch -D <分支名字>
```
### 创建分支并且直接切换到分支
```bash
    git checkout -b <新的分支名字>
```
### 合并分支
```bash
    git merge <分支名字>
```
### 现在最近当前分支提交的信息
```bash
    git branch -v
```
### 终止合并
```bash
    git merge --abort
```
### git 回退版本
```bash
    git reset --hard HEAD^ # 回退1个版本
    git reset --hard HEAD~1 #回退N个版本 ~N
    git reset --hard <commitID> #回退到某个版本
    git checkout <commitId> #切换到某次提交点  处于游离状态
```
### git 选择版本
```bash
    git reflog #查看操作日志
    # 找到commit日志 
    git reset --hard <commitID> #重新回到这个版本
```
### 分支 改名
```bash
    git branch -m <分支名> <新分支名>
```
### 临时保存
```bash
    git stash
    git stash save <备注说明> # 临时保存 并且添加说明
```
### 查看临时保存列表
```bash
    git stash list
```
### 临时保存 恢复
```bash
    git stash pop #恢复上一个临时保存  并且删除
    git stash apply #合并多个临时保存
    git stash apply stash@{0} # {N} N是数字 从git stash list 查看
```
### 删除临时保存
```bash
    git stash drop stash@{0} # {N} N是数字
```
### 创建标签
```bash
    git tag <标签名> # 简单标签
    git tag -a <标签名> -m <备注信息> # 详细标签
```
### 查看标签
```bash
    git tag # 查看标签    
    git tag -l 'XXX' # 精确查找
    git tag -l '*X' # 模糊查找
```
### 删除标签
```bash
    git tag -d <标签名>
```
### 查看文件修改者
```bash
    git blame <文件名>
```
### git diff (不加参数代表 工作区和暂存区全部的文件 做比较)
### git diff <文件名> ( 工作区和暂存区 单个文件 做比较)
```bash
    $ git diff # 命令
    # a/test01.txt 代表暂存区的文件
    # b/test01.txt 代表工作区的文件
    diff --git a/test01.txt b/test01.txt
    index 5f2f16b..ea6fb96 100644
    --- a/test01.txt
    +++ b/test01.txt
    # -1 -代表暂存区的文件 1代表有1行
    # +1 +代表工作区的文件 4代表有4行
    @@ -1 +1,4 @@
    # 代表工作区比暂存区多一行  000
    +000
    # 没有符号代表一样
    1111
    # 代表工作区比暂存区多一行  222
    +222
    # 代表工作区比暂存区多一行  333
    +333
    # 代表工作区比暂存区少一行  444
    -444
    # 代表工作区比暂存区多一行  (空行)
    +
```
### git diff <commitId> (加上commitId 代表 工作区和提交的快照 作比较)
```bash
    git diff HEAD # 当前工作区 和 最近一次提交 比较
    git diff <commitId> # 当前工作区 和 某次提交 比较
```
### git diff --cached (不加参数 代表 暂存区 和 最新的提交 做比较)
```bash
    git diff --cached
    git diff --cached <commitId>
```
### 推送到远程仓库
```bash
    git remote add origin <URL>
    git push -u origin master
```
### 查看远程仓库信息
```bash
    git remote show #查看全部的仓库
    git remote show origin(仓库名) #查看origin的详细信息
```