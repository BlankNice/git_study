### 查看版本
    $ git --version
---
### 用户配置
    用户名字：$ git config --global user.name "BlankNice"
    用户邮箱：$ git config --global user.email "1604171529@qq.com"
---
### 查看配置
    $ git config --list
---
### 区域
    工作区
    暂存区
    版本库
---
### 对象
    Git对象
        $ git hash-object -w 文件路径
            key:val 组成的键值对（key是val对应hash）
            键值对在git内部是一个 bolb 类型
    tree对象
        $ git update-index -add --cacheinfo 100644 哈希值 文件.txt
            往暂存区添加一条记录
        $ git write-tree
            生成树对象
    commit对象
        echo "first commit" | git commit-tree 哈希值（树对象）
            生成提交对象 
    $ git cat-file -p 哈希值
            查看对应对象的内容
    $ git cat-file -t 哈希值
            查看对应对象的类型
--- 
### linux基本命令
    清屏：$ clear
    输出内容到文件里：$ echo "git study" > test.txt
    查看子级目录：$ ll
    查看后代目录：$ find
                 $ find ./ -type f
    重命名：$ mv file.txt file666.txt
    删除：$ rm file.txt
    查看文件内容：$ cat file.txt
    进入文件编辑模式：$ vim file.txt
                    按i进入编辑
                    按esc和冒号:进入命令执行
                        q!强制退出
                        输入wq回车保存
                        set nu设置行号
---
### git操作最基本的流程
    常见工作目录 对工作目录进行修改
    git add ./
        git hash-object -w 文件名（修改了多少个工作目录中的文件 此命令就要被执行多少次）
        git update-index ...
    git commit -m "注释内容"
        git write-tree
        git commit-tree
---
### git高层命令（CRUD）
    $ git init                 初始化仓库
    $ git ls-files -s          查看暂存区
    $ git status               查看文件的状态（已跟踪（已提交 已暂存 已修改） 未跟踪）
    $ git diff                 查看哪些文件没有暂存
    $ git diff --staged        查看哪些文件已经暂存但没有提交
    $ git log --oneline        查看提交的历史记录
    $ git config --global alias.logall "log --oneline --decorate --graph --all"             配置别名为logall（查看分支历史记录）
    $ git add ./               将修改添加到暂存区
    $ git rm ./content.txt     删除工作目录中对应文件 再将修改文件添加到暂存区
    $ git mv one.txt two.txt   将工作目录中的文件进行重命名 再将修改添加到暂存区
    $ git commit -m ""         将暂存区提交到版本库
    $ git commit               需要开启文本注释
    $ git commit -a -m ""      跳过暂存区直接提交
---
### git高层命令（分支）
    $ git branch                显示分支列表
    $ git branch -v             查看分支指向的最新提交
    $ git branch 分支名          创建分支
    $ git branch 分支名 哈希值    在指定提交对象上创建新的分支
    $ git checkout 分支名        切换分支
    $ git branch -d 分支名       删除空的分支 删除已经被合并的分支
    $ git branch -D 分支名       强制删除分支
---
### reset（三部曲）
    $ git log
    $ git reflog                主要是HEAD有变化 那么git reflog就会记录下来
    三部曲：
        第一部： git reset --soft HEAD~
                只动HEAD（带着分支一起动）
        第二部： git reset --mixed HEAD~
                动HEAD（带着分支一起动）
                动了暂存区
        第三部： git reset --hrad HEAD~
                动HEAD（带着分支一起动）
                动了暂存区
                动了工作目录
---
### checkout
    $ git checkout commithash
    $ git checkout -- filename
        会动了工作目录
    $ git git reset --hrad commithash
        1. checkout只动HEAD
           --hard动HEAD而且带着分支一起走
        2. checkout 对工作目录是安全的
           --hard是强制覆盖工作目录
---
### 路径reset
    $ git reset [--mixed] HEAD filename    （reset将会跳过第1步）
            动了暂存区