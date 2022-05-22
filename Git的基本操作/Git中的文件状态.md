###Git仓库初始化
- 在项目的根目录中点击git bash here 然后在控制台中输入git init就可以创建初始化仓库,然后会出现.git隐藏目录  这个目录就是仓库
    

###Git文件的4种状态

- Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged

- Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件

- Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改

- Staged: 暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified



查看文件状态
上面说文件有4种状态，通过如下命令可以查看到文件的状态：

#####跟踪新文件
    `git add 文件名`
    git add有三个功能
    1.可以用它跟踪新文件
    2.可以把已跟踪的已修改的文件放到暂存区
    3.把有冲突的文件标记为已解决状态

#####查看指定文件状态
    git status [filename]
#####查看所有文件状态
    git status
#####精简的方式显示文件状态
    git status -s
#####提交更新(将文件提交到暂存区(staged))
    git commit -m "提交时要提醒的内容"
#####当git库中的文件被修改后，status的状态会被改为modified(已修改)
    红的modified是还未被放入暂存区的已修改文件
    绿色的modified表示放入暂存区的已修改文件

###git的原理
>首先未被git.add的文件状态是Untracked(未被跟踪) add之后状态改为Unmodified(未修改),一旦文件被修改之后,状态就会变成modified(已修改)
