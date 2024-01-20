集中式
共享的存储库
分布式
每个开发人员在他们的机器上都有一个存储库
但也有一个中央存储库


### 开源项目 Integration Manager workflow

维护者和许多贡献者,贡献者不被信任
只有项目的维护者有权利push
如果你想贡献,应该 fork 项目存储库在云中获取此存储库的副本
接下来我们克隆这个存储库到本地
写代码, push到我们forked的存储库
#### pull request
接下来我们发送一个请求(pull request)给维护者
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119171640.png)
这是github内置的功能
维护者会收到通知审查代码
他们可以pull our changes to review
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119172053.png)

如果觉得可以合并,他们就合并我们的代码到他们的本地仓库
然后push到他们的远程库


### Creating a GitHub Repository
```
设置为私有我们选择谁可以看到并提交到这个存储库
要使用私有存储库，我们必须付费

add a README file 时,github会为我们创建第一个提交
当前的分支是 master
```
### Adding Collaborators

```
添加你的团队成员,给他们推送权限
设置->我们的团队成员 全名或电子邮件

一旦我接受了邀请
我将拥有对该存储库的推送访问权限


```


![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119173850.png)
### Cloning a Repository

```
每个团队成员都应该克隆这个存储库
git clone 存储库的完整 URL

git 克隆整个仓库 all the commits

git log --oneline --all --graph 

when we clone a repository
git names the source repository(远程)
git names that origin
origin is a reference to 远程 repository
```
#### origin/main 
technically this is called a remote tracking branch
```
# 告诉我们我们在远程仓库的main分支
tells us where is the main branch in 远程 repository

it's not a kind of branch you are familiar with
we cannot check it out we cannot commit to it

if we git switch origin/master # get error

git branch # master


```
#### origin/HEAD
tell us where is the head pointer in our origin repository
#### git remote
shows the list of remote repositories # origin
```
git remote -v
// origin 引用的 仓库
origin https://github.com/tianran721/Objsidian (fetch)
origin https://github.com/tianran721/Objsidian (push)

```



### Fetching
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119181054.png)

```
目前本地库还未连接到远程库,所以当远程库里有了新的提交,我们的本地库是不知道的

我们必须使用fetch命令,下载远程库的新提交到本地,origin/master将会自动往前移动

origin/master 是远程跟踪分支,告诉我们origin的master在哪,现在指向B

git fetch # git 默认fetch 从origin
git fetch origin # fetch origin所有分支
git fetch origin xxx # 只fetch xxx branch

```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119181454.png)

#### git merge origin/main
```
目前maste指向A,我们需要将B分支合并到master
所以我们切换到master分支,执行  git merge origin/main

cat README.md # 终端查看
```

git branch
```
git branch -vv
# it shows how our local and remote tracking branches are diverging
```

### Pulling
[[git config#pull 配置]]
 
pull = fetch + merge/rebase 
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119184214.png)

```
当执行git pull --no-rebase 命令
将下载C 到本地库,同时master/main将会指向c,git会创建新历史并将B和C合并到新的历史,此时历史不再是线性的

# merge 合并会产生新历史,有人更喜欢rebase

```
#### git pull -rebase

```
使用rebase会改变master的基类,使用前master的基类是A
使用后会变成C
最终得到的历史如下图, 历史还是线性的

```
![](https://raw.githubusercontent.com/tianran721/img/main/img/20240119195906.png)
实操

```
远程库添加一行代码

本地添加代码:
1. echo hello > file1.txt
2. git add .
3. git commit -m "add file1"
此时master分支和 origin/main分支 分歧了

# 退回上次历史
git reset --hard HEAD~1

# rebase 会把本地和远程合并到新分支,历史是线性的
git pull --rebase 

```

### pushing

```
# push时需要远程仓库名 and branch
git push # assume origin by default
git push origin # main by default
git push origin main

如果没有弄ssh , 需要Github credentials 也就是账号密码
```
#### push前的操作
```
当我们push前,有别人向远程代码库提交代码,远程形成新的commit,此时我们push到远程库会被拒绝
如果使用 git push -f ,那远程库会删掉上一个人提交的历史,替换成你提交的历史
(丧良心)

正确做法:
先git pull merge或者rebase 解决冲突 , 再去push


```

### Storing Credentials


```
git config --global credential.helper cache 将凭证存放在内存中一段时间

如果想把登录凭证永久存储到电脑
mac 使用keychain
windows使用  Windows credentials Store

git credential-osxkeychain # 查看mac是否安装
# usage: git credential-osxkeychain <get|store|erase> : 安装了

然后我们配置凭证
git config --global credential.helper osxkeychain

```

###  Sharing Tags

```
默认push不会把tag发给远程库

git tag v1.0 # tag会添加到最新的历史

# push时把tag也push上去 注意要带上分支名

git push origin v1.0 

github会自动生成包给我们

# 删除tag , 但是tag依然存在在本地
git push origin --delete v1.0

# 本地删除tag
git tag -d v1.0

```

### Releases

```
github 可以通过release打包软件
1. create  a new release 
2. choose a tag
3. title
4. release note
5. Attach binaries by dropping them here or selecting them.(把编译后的二进制程序拖上去)
6. 发布
```
### Sharing Branches

```
和分享Tag类似

# 创建分支 (包括所有旧分支的代码)
git switch -C feature/change-password

直接push会提示分支 no upstream

# 查看本地 和远程追踪分支

git branch -vv

# 查看左右远程追踪分支

git branch -R

# 新分支push到远程库
-u is the short of set upstream , 后面是 运程引用 和分支名

git push -u origin feature/change-password

```
#### 删除分支
```
# d: delete
git push -d origin son

注意本地的 son 分支没有删除, 我们需要switch到本地main分支 删除本地分支

git switch main
git merge son 


```

### Collaboration Workflow (add a feature)

#### 组长视角
```
 1.远程库创建son分支
 
 # git fetch 只是得到了远程追踪分支, 我们还需要在本地创建私有分支 map到远程追踪分支
 git fetch origin son 

git switch -C son origin/son
执行后终端输出: 分支 'son' 设置为跟踪 'origin/son'。 切换到并重置分支 'son'。 您的分支已与 'origin/son' 保持最新。

```

#### tom视角

```
# tom文件下
git clone git@github.com:tianran721/Objsidian.git
# 进入仓库
cd xxx
# 查看branch , 并没有son分支
git branch 
# tom应该创建分支map 远程son分支

git switch -C son origin/son

# tom 写代码并提交
echo tom write code > file1.txt
# -am `-a` 表示自动将所有已修改的文件添加到暂存区，
git commit -am "update file1"

git push origin son

```
#### 组长视角 : 合并tom的son到master,关闭son分支 
```

git pull origin son
# 注意 保持本地,远程分支执行一致
git switch main
git merge son
git push origin main
# 删除远程son分支

git push -d origin son
# 删除本地son
git branch -d son

# 检查 本地分支和远程分支
git branch
git branch -r 

```

#### tom视角
pull取main分支并删除本地son分支
```
# 即使远程组长已经删除了 son分支

当执行 git branch -r 发现 远程追踪son分支还在

# 要想删除 我们应该执行

git remote prune origin 

```