### 三个必须懂得概念
    本地分支
    远程跟踪分支（remote/分支名）
    远程分支
---
### SSH
    $ ssh-keygen -t -rea -C "1604171529@qq.com"
    C:\Users\Administrator\.ssh                     文件位置
    ssh -T git@github.com                           测试公钥是否已经配对
---
### 远程协作的基本流程
    第一步：项目经理创建一个空的远程仓库
    第二步：项目经理创建一个待推送的本地仓库
    第三步：为远程仓库配别名 配完用户名 邮箱
    第四步：在本地仓库中初始化代码 提交代码
    第五步：推送
    第六步：邀请成员
    第七步：成员克隆远程仓库
    第八步：成员做出修改
    第九步：成员推送自己的修改
    第十步：项目经理拉取成员的修改
---
### 做跟踪
    克隆仓库是 会自动为master做跟踪
    本地没有分支
        $ git checkout --track 远程跟踪分支（origin/分支名）
    本地已经创建了分支（比如：当前分支为 dev）
        $ git branch -u 远程跟踪分支（origin/分支名）
    $ git push                  推送
    $ git pull                  拉取
---
### 忽略文件
    .gitignore
        .DS_Store
        node_modules/
        /dist/
---
### 常用命令
    $ git status
    $ git log --oneline --decorate --graph --all        可以配置别名 logall
    $ git add ./
    $ git commit -m "注释内容"
    $ git commit -a -m "注释内容"                        已跟踪后可以跳过 git add
    $ git checkout -b branchname                        切换并创建分支
    $ git checkout branchname                           切换分支
    $ git push
    $ git fetch
    $ git pull