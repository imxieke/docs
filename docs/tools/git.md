# Git 小记

`.gitkeep` 的作用是为了提交空文件夹

## 常用命令
```shell
git add
git commit -m "commit log"
git push -u origin <branch example:master>
git status
git log --pretty=format:"%d %cn %cd" --graph
git log --since=2.weeks
git branch testing 			//create new branch
git checkout testing 		//切换分支
git checkout -b testing 	//equal git branch && git checkout
git filter-branch --tree-filter 'rm -f WebRoot/WEB-INF/lib/*.jar' --tag-name-filter cat -- --all //删除历史文件
git push origin --tags --force
git push origin --all --force
```
### 选项   说明
```
%H  提交对象（commit）的完整哈希字串
%h  提交对象的简短哈希字串
%T  树对象（tree）的完整哈希字串
%t  树对象的简短哈希字串
%P  父对象（parent）的完整哈希字串
%p  父对象的简短哈希字串
%an 作者（author）的名字
%ae 作者的电子邮件地址
%ad 作者修订日期（可以用 -date= 选项定制格式）
%ar 作者修订日期，按多久以前的方式显示
%cn 提交者(committer)的名字
%ce 提交者的电子邮件地址
%cd 提交日期
%cr 提交日期，按多久以前的方式显示
%s  提交说明

选项 说明
-p 按补丁格式显示每个更新之间的差异。
--stat 显示每次更新的文件修改统计信息。
--shortstat 只显示 --stat 中最后的行数修改添加移除统计。
--name-only 仅在提交信息后显示已修改的文件清单。
--name-status 显示新增、修改、删除的文件清单。
--abbrev-commit 仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。
--relative-date 使用较短的相对时间显示（比如，“2 weeks ago”）。
--graph 显示 ASCII 图形表示的分支合并历史。
--pretty 使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。
```

## 从历史记录中删除文件
```
git rm --cached filename
git commit --amend -AHEAD
```


#### Fork仓库同步
从源代码仓库Fork一份后，希望Fork能与源项目更新保持一致，又保留我们自己的修改

整个同步过程需要两步来完成，具体来说：

一、配置上游仓库

1、先使用 git remote -v 查看一下当前的远程仓库状态
```
git remote -v
# origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
# origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```
2、给Fork仓库添加一个远程的上游仓库

     git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
3、确认是否添加成功
```
git remote -v
# origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
# origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
# upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
# upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
```

二、同步Fork仓库

1、从上游仓库 fetch 分支和提交点，并会被储存在本地分支： upstream/master
```
git fetch upstream
# remote: Counting objects: 85, done.
# remote: Compressing objects: 100% (88/88), done.
# remote: Total 92 (delta 43), reused 45 (delta 12)
# Unpacking objects: 100% (88/88), done.
# From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
#  * [new branch]      master     -> upstream/master
```
2、切换到本地 master 分支
```
git checkout master
# Switched to branch 'master'
```
3、把 upstream/master 分支合并到本地 master 上，这样就完成了同步，并且不会丢掉本地修改的内容
```
git merge upstream/master
# Updating f343234..93kfw23
# Fast-forward
#  README                    |    22 -------
#  README.md                 |    11 ++++++
#  2 files changed, 11 insertions(+), 22 deletions(-)
#  delete mode 100644 README
#  create mode 100644 README.md
```

Github offcial Example
…or create a new repository on the command line

```
echo # XCloud >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/imxieke/XCloud.git
git push -u origin master
```

…or push an existing repository from the command line
```
git remote add origin https://github.com/imxieke/XCloud.git
git push -u origin master
```

# Tips: 
 
    git config -l        查看当前用户信息
    git config --global user.email "im@xieke.org"
    git config --global user.name "imxieke"
    git rm      ---git delete command
    git add filename1.md filename2.txt filename3.php     多个使用空格分开
    git add .        .代表所有文件
    git add -a       代表所有文件
    git add -a :/    代表所有文件
    git add -A
    git add -A :/
    git push -f 强制将本地代码推送到服务器的仓库中

顺序为：
    
    git clone XXXXXX
    git add .  //.代表全部 或 -A 代表全部
    git commit -m "commit content " 
    git commit -a -m 'this is memo'  //此与上串重复 功能不同！
    git remote add origin https://git.coding.net/xxx/xxx.git  在没有Clone情况下使用，增加远程代码；
    git push  -u origin master //指定远程分支，默认git push 即可

### commit和commit -a的区别, commit -a相当于：

    第一步：自动地add所有改动的代码，使得所有的开发代码都列于index file中；
    第二步：自动地删除那些在index file中但不在工作树中的文件，即Clone到本地后被修改或删除的；
    第三步：执行commit命令来提交；
    

在git中如果想忽略掉某个文件，不让这个文件提交到版本库中，可以使用修改根目录中 .gitignore 文件

# 此为注释 – 将被 Git 忽略
 
    *.a       # 忽略所有 .a 结尾的文件
    !lib.a    # 但 lib.a 除外
    /TODO     # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
    build/    # 忽略 build/ 目录下的所有文件
    doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt

>某些目录或文件加入忽略规则无效是因为.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未track状态）

    git rm -r --cached .
    git add .
    git commit -m 'update .gitignore'

### Github的提交方式 

     （1）git add .--------------------存储到本地 
         git commit -m 'message'-------存储时的标记（修改了哪些地方，方便下次查询） 
         git pull------------------------下载服务器代码 
         git push------------------------上传代码至服务器 

  ### svn服务器的提交方式 
   
    git add .  ------------------存储到本地 
    git commit -m 'message'--------存储时的标记（修改了哪些地方，方便下次查询） 
    git svn rebase------------------下载服务器代码 
    git svn dcommit-----------------上传代码至服务器 
   
### 其他相关的git命令 

Git Branch-------------------查看当前属于哪个分支 

    只有冲突存在时才会修改分支——改为冲突再git add . 
    git rebase –-continue-------------------自动合并 
    git checkout –b svn 新建分支名----------新建分支存储现有文件 
    git branch-------------------------------查看在哪个分支下 
    git checkout master----------------------将其放到master分支下 
    git merge-------------------------------整合分支 
    git branch -d 分支名----------------------删除分支 
    git checkout + 上传的commit编号-----------将本地代码恢复到此状态 
    git log------------------------------------查看本地git上传日志 
    git log -p app/controllers/grids_controller.rb----查看某个文件的修改历史 
    git checkout d0eb6ef3afe8a377943d3cf6f1e9c320c18f6f32 
    app/controllers/charts_controller.rb-----------返回到这个版本的文件（重现错误） 
    git diff ＋ commit编号--------------------------查询不同代码

### GIT常用命令
日常工作中推荐使用Git第三方GUI工具SourceTree，当然，Git的命令还是需要备注一下：
查看、添加、提交、删除、找回，重置修改文件

    git help <command> # 显示command的help
    git show # 显示某次提交的内容 git show $id
    git co — <file> # 抛弃工作区修改
    git co . # 抛弃工作区修改
    git add <file> # 将工作文件修改提交到本地暂存区
    git add . # 将所有修改过的工作文件提交暂存区
    git rm <file> # 从版本库中删除文件
    git rm <file> –cached # 从版本库中删除文件，但不删除文件
    git reset <file> # 从暂存区恢复到工作文件
    git reset — . # 从暂存区恢复到工作文件
    git reset –hard # 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改
    git ci <file> git ci . git ci -a # 将git add, git rm和git ci等操作都合并在一起做
    git ci -am “some comments”
    git ci –amend # 修改最后一次提交记录
    git revert <$id> # 恢复某次提交的状态，恢复动作本身也创建次提交对象
    git revert HEAD # 恢复最后一次提交的状态

### 查看文件diff

    git diff <file> # 比较当前文件和暂存区文件差异 git diff
    git diff <$id1> <$id2> # 比较两次提交之间的差异
    git diff <branch1>..<branch2> # 在两个分支之间比较
    git diff –staged # 比较暂存区和版本库差异
    git diff –cached # 比较暂存区和版本库差异
    git diff –stat # 仅仅比较统计信息

### 查看提交记录

    git log git log <file> # 查看该文件每次提交记录
    git log -p <file> # 查看每次详细修改内容的diff
    git log -p -2 # 查看最近两次详细修改内容的diff
    git log –stat #查看提交统计信息

## tig
`macOS`上可以使用 `tig` 代替 `diff` 和 `log` ，`brew install tig`
Git 本地分支管理

###  查看、切换、创建和删除分支
```
git br -r # 查看远程分支
git br <new_branch> # 创建新的分支
git br -v # 查看各个分支最后提交信息
git br –merged # 查看已经被合并到当前分支的分支
git br –no-merged # 查看尚未被合并到当前分支的分支
git co <branch> # 切换到某个分支
git co -b <new_branch> # 创建新的分支，并且切换过去
git co -b <new_branch> <branch> # 基于branch创建新的new_branch
git co $id # 把某次历史提交记录checkout出来，但无分支信息，切换到其他分支会自动删除
git co $id -b <new_branch> # 把某次历史提交记录checkout出来，创建成一个分支
git br -d <branch> # 删除某个分支
git br -D <branch> # 强制删除某个分支 (未被合并的分支被删除的时候需要强制)
```

## 分支合并和rebase
```
git merge <branch> # 将branch分支合并到当前分支
git merge origin/master –no-ff # 不要Fast-Foward合并，这样可以生成merge提交
git rebase master <branch> # 将master rebase到branch，相当于： git co <branch> && git  rebase master && git co master && git  merge <branch>
```

## Git补丁管理(方便在多台机器上开发同步时用)
```
git diff > ../sync.patch # 生成补丁
git apply ../sync.patch # 打补丁
git apply –check ../sync.patch #测试补丁能否成功
```

## Git暂存管理
```
git stash # 暂存
git stash list # 列所有stash
git stash apply # 恢复暂存的内容
git stash drop # 删除暂存区
```

## Git远程分支管理
```
git pull # 抓取远程仓库所有分支更新并合并到本地
git pull –no-ff # 抓取远程仓库所有分支更新并合并到本地，不要快进合并
git fetch origin # 抓取远程仓库更新
git merge origin/master # 将远程主分支合并到本地当前分支
git co –track origin/branch # 跟踪某个远程分支创建相应的本地分支
git co -b <local_branch> origin/<remote_branch> # 基于远程分支创建本地分支，功能同上
git push # push所有分支
git push origin master # 将本地主分支推到远程主分支
git push -u origin master # 将本地主分支推到远程(如无远程主分支则创建，用于初始化远程仓库)
git push origin <local_branch> # 创建远程分支， origin是远程仓库名
git push origin <local_branch>:<remote_branch> # 创建远程分支
git push origin :<remote_branch> #先删除本地分支(git br -d <branch>)，然后再push删除远程分支
```

## Git远程仓库管理
```
git remote -v # 查看远程服务器地址和仓库名称
git remote show origin # 查看远程服务器仓库状态
git remote add origin git@ github:robbin/robbin_site.git # 添加远程仓库地址
git remote set-url origin git@ github.com:robbin/robbin_site.git # 
设置远程仓库地址(用于修改远程仓库地址) git remote rm <repository> # 删除远程仓库
```

## 创建远程仓库
```
git clone –bare robbin_site robbin_site.git # 用带版本的项目创建纯版本仓库
scp -r my_project.git git@ git.csdn.net:~ # 将纯仓库上传到服务器上
mkdir robbin_site.git && cd robbin_site.git && git –bare init # 在服务器创建纯仓库
git remote add origin git@ github.com:robbin/robbin_site.git # 设置远程仓库地址
git push -u origin master # 客户端首次提交
git push -u origin develop # 首次将本地develop分支提交到远程develop分支，并且track
git remote set-head origin master # 设置远程仓库的HEAD指向master分支也可以命令设置跟踪远程库和本地库
git branch –set-upstream master origin/master
git branch –set-upstream develop origin/develop
```
-------------------------------------------------------------------------------

## From OSC
 
   与其他技术相比，Git应该拯救了更多开发人员的饭碗。只要你经常使用Git保存自己的工作，你就一直有机会可以将代码退回到之前的状态，因此就可以挽回那些你深夜里迷迷糊糊犯下的错误。

尽管这么说，Git的命令行界面可是出了名的难掌握。接下来，就给大家介绍7个小技巧，最大限度发挥Git的作用。

通常，大部分时间我们都只会用到`add`、`commit`、`branch`和`push/pull`这 些命令。大部分人熟悉这套只往一个方向运转的工作流。你们有没有想过，如果自己往仓库中添加了错误的文件，或是将代码提交到了错误的分支，而且提交信息还 写错了的话，自己怎样才能取消之前的操作？如果你也是按照上面漫画中所描绘的一样操作的（即删除本地项目文件夹，再重新下载仓库），那么你就有必要了解下 面这些Git使用技巧了。
 ![图片](https://dn-coding-net-production-pp.qbox.me/1502767a-b7db-4bcb-a05e-c12010d2da4f.png) 
1. 修改错误的提交信息（commit message）

提交信息很长时间内会一直保留在你的代码库（code base）中，所以你肯定希望通过这个信息正确地了解代码修改情况。 下面这个命令可以让你编辑最近一次的提交信息，但是你必须确保没有对当前的代码库（working copy）做修改，否则这些修改也会随之一起提交。

    $ git commit --amend -m ”YOUR-NEW-COMMIT-MESSAGE”

假如你已经将代码提交（git commit）推送（git push）到了远程分支，那么你需要通过下面的命令强制推送这次的代码提交。

    $ git push <remote> <branch> --force

你可以关注[Stack Overflow](http://www.stackoverflow.com)网站上的这条问答， 获取更多详情。

2. 提交之前撤销git add

如果你往暂存区（staging area）中加入了一些错误的文件，但是还没有提交代码。你可以使用一条简单的命令就可以撤销。如果只需要移除一个文件，那么请输入：

    $ git reset <文件名>

或者如果你想从暂存区移除所有没有提交的修改：

    $ git reset

你可以关注Stack Overflow网站上的这条问答， 获取更多详情。

3. 撤销最近一次代码提交

有时候你可能会不小心提交了错误的文件或一开始就遗漏了某些东西。下面这三步操作可以帮助你解决这个问题。

    $ git reset --soft HEAD~1

### 对工作文件进行必要的更改

    $ git add -A .
    $ git commit -c ORIG_HEAD

你执行第一个命令时，Git会将HEAD指针（pointer）后移到此前的一次提交，之后你才能移动文件或作必要的修改。

然后你就可以添加所有的修改，而且当你执行最后的命令时，Git会打开你的默认文本编辑器，其中会包含上一次提交时的信息。如果愿意的话，你可以修改提交信息，或者你也可以在最后的命令中使用-C而不是-c，来跳过这一步。

    Git + spaghetti = spagitty

4. Git仓库撤销至前一次提交时的状态

“撤销”（revert）在许多情况下是非常有必要的——尤其是你把代码搞的一团糟的情况下。最常见的情况是，你想回到之前代码版本，检查下那个时候的代码库，然后再回到现在状态。这可以通过下面的命令实现：

$ git checkout <SHA>

“”是你想查看的提交拥有的哈希值（Hash Code）中前8至10个字符。 这个命令会使<HEAD>指针脱离（detach），可以让你在不检出（check out）任何分支的情况下查看代码——脱离HEAD并不像听上去那么可怕。如果你想在这种情况下提交修改，你可以通过创建新的分支来实现：

    $ git checkout -b <SHA>

要想回到当前的工作进度，只需要检出（check out）你之前所在的分支即可。

你可以关注Stack Overflow网站上的这条问答， 获取更多详情。

5. 撤销合并（Merge）

要想撤销合并，你可能必须要使用恢复命令（HARD RESET）回到上一次提交的状态。“合并”所做的工作基本上就是重置索引，更新working tree（工作树）中的不同文件，即当前提交（）代码中与HEAD游标所指向代码之间的不同文件；但是合并会保留索引与working tree之间的差异部分（例如那些没有被追踪的修改）。

    $ git checkout -b <SHA>

当然，Git中总是有其他的实现办法，你可以查看看这篇文章继续了解。

从当前Git分支移除未追踪的本地文件

假设你凑巧有一些未被追踪的文件（因为不再需要它们），不想每次使用git status命令时让它们显示出来。下面是解决这个问题的一些方法：

    $ git clean -f -n         # 1
    $ git clean -f            # 2
    $ git clean -fd           # 3
    $ git clean -fX           # 4
    $ git clean -fx           # 5

(1): 选项-n将显示执行（2）时将会移除哪些文件。
(2): 该命令会移除所有命令（1）中显示的文件。
(3): 如果你还想移除文件件，请使用选项-d。
(4): 如果你只想移除已被忽略的文件，请使用选项-X。
(5): 如果你想移除已被忽略和未被忽略的文件，请使用选项-x。

请注意最后两个命令中X的区别。

更多详情，请查看官方文档中关于[git-clean](http://git-scm.com/docs/git-clean)的介绍。
 删除本地和远程Git分支

删除本地分支：

    $ git branch --delete --force <branchName>

或者使用选项-D作为简写：

    $ git branch -D

删除远程分支：

    $ git push origin --delete <branchName>

建议：要想更好地掌握Git的用法，请仔细阅读Git官方文档。

## Fork仓库同步
当我们从源代码仓库Fork一份后，我们既希望Fork能与源项目更新保持一致，又希望能保留我们自己的修改，下面我来讲一下实现。

整个同步过程需要两步来完成，具体来说：

一、配置上游仓库

1、先使用 git remote -v 查看一下当前的远程仓库状态
```
git remote -v
# origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
# origin  https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
```
2、给Fork仓库添加一个远程的上游仓库

     git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
3、确认是否添加成功
```
git remote -v
# origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
# origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
# upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
# upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
```
二、同步Fork仓库

1、从上游仓库 fetch 分支和提交点，并会被储存在本地分支： upstream/master
```
git fetch upstream
# remote: Counting objects: 85, done.
# remote: Compressing objects: 100% (88/88), done.
# remote: Total 92 (delta 43), reused 45 (delta 12)
# Unpacking objects: 100% (88/88), done.
# From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
#  * [new branch]      master     -> upstream/master
```
2、切换到本地 master 分支
```
git checkout master
# Switched to branch 'master'
```
3、把 upstream/master 分支合并到本地 master 上，这样就完成了同步，并且不会丢掉本地修改的内容
```
git merge upstream/master
# Updating f343234..93kfw23
# Fast-forward
#  README                    |    22 -------
#  README.md                 |    11 ++++++
#  2 files changed, 11 insertions(+), 22 deletions(-)
#  delete mode 100644 README
#  create mode 100644 README.md
```

## 仓库瘦身
* 删除从现在到后面的所有 reflog 引用
- git reflog expire --expire=now --all
- 通过运行垃圾回收器和删除旧的对象重新打包仓库。
- git gc --prune=now
- 从历史记录删除文件
- git log --pretty=oneline --branches -- filename
- filter-branch 命令重写所有 commit 将文件从 Git 历史中完全移除
- git filter-branch --index-filter 'git rm --cached --ignore-unmatch filename '
- git filter-branch --force --index-filter "git rm --cached --ignore-unmatch $@" --prune-empty --tag-name-filter cat -- --all


## 强制覆盖 请勿用于生产环境
```
git fetch --all
git reset --hard origin/master
git pull
```

## 设置代理
```
git config --global https.proxy http://127.0.0.1:1080
git config --global https.proxy https://127.0.0.1:1080
git config --global http.proxy socks5://127.0.0.1:7890
git config --global https.proxy socks5://127.0.0.1:7890
git config --global --unset http.proxy
git config --global --unset https.proxy
# 只对 github.com
git config --global http.https://github.com.proxy socks5://127.0.0.1:1080
git config --global http.https://github.com.proxy socks5://127.0.0.1:7890
npm config delete proxy
```