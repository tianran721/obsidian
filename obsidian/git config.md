### Configuring Git

```
name
email
default editor 默认是使用VIM
line ending
```

```
SYSTEM All users
GLOBAL All repositories of the current user
LOCAL  The current repository

git config --global user.name "zhaofeng"
git config --global user.email 858448643@qq.com
// wait 告诉终端直到我们关闭vscode再继续执行
git config --global core.editor "code --wait"
// 打开config文件
git config --global -e

```

#### line ending

```
windows : adc\r\n
\r(Carriage Return 回车)
\n (Line Feed 换行)

mac/linux : abc\n

为了避免出现bug, 我们需要配置 core.autocrlf

# window 设置
git config --global core.autocrlf true
# mac/linus 设置
git config --global core.autocrlf input
```

#### pull 配置

```
 git config pull.rebase false  # merge

git config pull.rebase true   # rebase

git config pull.ff only       # fast-forward only

hint: You can replace "git config" with "git config --global" to set a default

hint: preference for all repositories. You can also pass --rebase, --no-rebase,

hint: or --ff-only on the command line to override the configured default per invocation.
```

```
我的配置
git config --global pull.rebase false

```

[[git collaboration#Storing Credentials]]
