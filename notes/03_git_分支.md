### git分支本质
    分支本质是一个提交对象，所有的分支都会有机会被HEAD所引用（HEAD一个时刻只会指向一个分支）
    当我们有新的提交对象的时候，HEAD会携带当前持有的分支往前移动
---
### git分支
    $ git branch branchname                 创建
    $ git checkout branchname               切换
    $ git checkout -b branchname            创建+切换
    $ git branch branchname commithash      版本穿梭（时光机）
    $ git branch -d branchname              普通删除
    $ git branch -D branchname              强制删除
    $ git merge branchname                  合并分支
        快进合并    不会产生冲突
        典型合并    有机会产生冲突
        解决冲突    打开冲突的文件 进行修改 add commit
    $ git branch                            查看分支列表
    $ git branch --merged                   查看合并到当前分支的分支
        一旦出现在这个列表中 就应该删除
    $ git branch --no-merged                查看没有合并到当前分支的分支列表
        一旦出现在这个列表中 就应该观察一下是否需要合并
### 分支的注意点
    在切换的时候一定要看一看 git status
        允许切换分支：
            分支上所有的内容出于 已提交状态
            (no) 分支上的内容是初始化创建 处于未跟踪状态
            (no) 分支上的内容是初始化创建 第一次处于已暂存状态
        不允许切分支：
            分支上所有的内容处于已修改状态 或 第二次以后的已暂存状态
    在分支上的工作做到一半时 如果有切换分支的需求 我们应该将现有的工作存储起来
    $ git stash                             会将当前分支上的工作推到一个栈中
        分支切换 进行其他工作 完成其他工作后 切回分支
    $ git stash apply                       将栈顶的工作内容还原 但不让任何内容出栈
    $ git stash drop                        取栈顶的工作内容后 就应该将其删除（出栈）
    $ git stash pop                         apply+drop
    $ git stash list                        查看存储
---
### git分支本质
    分支本质是一个提交对象，所有的分支都会有机会被HEAD所引用（HEAD一个时刻只会指向一个分支）
    当我们有新的提交对象的时候，HEAD会携带当前持有的分支往前移动
---
### git分支
    $ git branch branchname                 创建
    $ git checkout branchname               切换
    $ git checkout -b branchname            创建+切换
    $ git branch branchname commithash      版本穿梭（时光机）
    $ git branch -d branchname              普通删除
    $ git branch -D branchname              强制删除
    $ git merge branchname                  合并分支
        快进合并    不会产生冲突
        典型合并    有机会产生冲突
        解决冲突    打开冲突的文件 进行修改 add commit
    $ git branch                            查看分支列表
    $ git branch --merged                   查看合并到当前分支的分支
        一旦出现在这个列表中 就应该删除
    $ git branch --no-merged                查看没有合并到当前分支的分支列表
        一旦出现在这个列表中 就应该观察一下是否需要合并
### 分支的注意点
    在切换的时候一定要看一看 git status
        允许切换分支：
            分支上所有的内容出于 已提交状态
            (no) 分支上的内容是初始化创建 处于未跟踪状态
            (no) 分支上的内容是初始化创建 第一次处于已暂存状态
        不允许切分支：
            分支上所有的内容处于已修改状态 或 第二次以后的已暂存状态
    在分支上的工作做到一半时 如果有切换分支的需求 我们应该将现有的工作存储起来
    $ git stash                             会将当前分支上的工作推到一个栈中
        分支切换 进行其他工作 完成其他工作后 切回分支
    $ git stash apply                       将栈顶的工作内容还原 但不让任何内容出栈
    $ git stash drop                        取栈顶的工作内容后 就应该将其删除（出栈）
    $ git stash pop                         apply+drop
    $ git stash list                        查看存储
---
