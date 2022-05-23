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
>首先未被git.add的文件状态是Untracked(未被跟踪) add之后状态改为Unmodified(未修改),一旦文件被修改之后,状态就会变成红色的modified(已修改),再经过git.add之后状态就会变成绿色的modified,代表文件已被放入暂存区(Staged),最后git commit -m "注释"存入git仓库中


###撤销对文件的修改
>撤销对文件的修改，也就是把工作区中对应的文件还原成git仓库中所保存的版本,危险性较高，所有工作区中对文件的修改将丢失，且无法恢复

#####撤销步骤
    git checkout -- 文件名

#####一次性添加多个文件到暂存区
    git add .
#####从暂存区中移除对应的文件
    git reset HEAD 文件名
    移除多个:git reset HEAD .

#####跳过使用暂存区域
    git commit -a -m "注释", GIT就会自动把已跟踪的文件添加到库中，跳过暂存区

###移除文件
    1.从Git仓库和工作区中同时移除index.js文件
        git rm -f index.js
    2.只从仓库中移除index.css,但保留工作区中的index.css
        git rm --cached index.css
###忽略文件
    有一些文件无需纳入Git管理,也不希望他们出现再未跟踪列表,在这种情况下，可以创建一个名为.gitignore的配置文件,列出要忽略的文件的匹配模式
#####Git 忽略规则匹配语法
    空格不匹配任意文件，可作为分隔符，可用反斜杠转义
    
    开头的文件标识注释，可以使用反斜杠进行转义
    
    ! 开头的模式标识否定，该文件将会再次被包含，如果排除了该文件的父级目录，则使用 ! 也不会再次被包含。可以使用反斜杠进行转义
    
    / 结束的模式只匹配文件夹以及在该文件夹路径下的内容，但是不匹配该文件
    
    / 开始的模式匹配项目跟目录
    
    如果一个模式不包含斜杠，则它匹配相对于当前 .gitignore 文件路径的内容，如果该模式不  在 .gitignore 文件中，则相对于项目根目录
    
    ** 匹配多级目录，可在开始，中间，结束
    
    ? 通用匹配单个字符
    
    * 通用匹配零个或多个字符
    
    [] 通用匹配单个字符列表
#####常用匹配示例
    bin/: 忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
    
    /bin: 忽略根目录下的bin文件
    
    /*.c: 忽略 cat.c，不忽略 build/cat.c
    
    debug/*.obj: 忽略 debug/io.obj，不忽略 debug/common/io.obj 和 tools/debug/io.obj
    
    **/foo: 忽略/foo, a/foo, a/b/foo等
    
    a/**/b: 忽略a/b, a/x/b, a/x/y/b等
    
    !/bin/run.sh: 不忽略 bin 目录下的 run.sh 文件
    
    *.log: 忽略所有 .log 文件
    
    config.php: 忽略当前路径的 config.php 文件

        

        
