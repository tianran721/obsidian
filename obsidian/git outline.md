1- Introduction
2- How to Take This Course
3- What is Git
4- Using Git
5- Installing Git

# 6- Configuring Git

[[git config]]

```
~/.gitconfig # config file
```

7- Getting Help
8- Cheat Sheet
1- Introduction
2- Initializing a Repository
3- Git Workflow
4- Staging Files
5- Committing Changes
6- Committing Best Practices
7- Skipping the Staging Area
8- Removing Files
9- Renaming or Moving Files
10- Ignoring Files

# 11- Short Status

```
git status -s 
红色代表在工作区的文件
绿色代表在stage 区

# 当我们将文件放入暂存区时,git会把文件的快照放入暂存区

# 当修改已经在暂存区的文件时,我们需要再次更新快照到暂存区
```

12- Viewing Staged and Unstaged Changes

# 13- Visual Diff Tools

```
# 配置系统diff工具 vscode
git config --global diff.tool vscode
# vscode diff时 会执行的命令 知道关闭diff窗口
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE" ($LOCAL $REMOTE需要在配置文件上手写上)

# query config
git config --global -e

# 使用difftool命令 
git difftool # diff 工作区和暂存区 ,两个区没差异就什么都不会做
git difftool --staged # diff staged file


```

14- Viewing History
15- Viewing a Commit
16- Unstaging Files
17- Discarding Local Changes
18- Restoring a File to an Earlier Version
19- Creating Snapshots with VSCode

```
source control usage
TIMELINE # 查看单个文件历史
```

20- Creating Snapshots with GitKraken

1- Introduction
2- Getting a Repository
3- Viewing the History
4- Filtering the History
5- Formatting the Log Output
6- Aliases
7- Viewing a Commit
8- Viewing the Changes Across Commits
9- Checking Out a Commit

```

```

10- Finding Bugs Using Bisect
11- Finding Contributors Using Shortlog
12- Viewing the History of a File
13- Restoring a Deleting File
14- Finding the Author of Line Using Blame
15- Tagging
16- Browsing History Using VSCode

```
安装 gitlens 
```

17- Browsing the History Using GitKraken
1- Introduction
2- What are Branches
3- Getting a Repository
4- Working with Branches
5- Comparing Branches

## 6- Stashing

## Fast-forward merges

```
# a branch is just a pointer to commit
如果两个分支没有分开,历史是线性的,git执行fast-forward merge,
只是把源指针前移,然后删除创建分支的pointer
```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240120111703.png)

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240120111645.png)

### 3-way merges

```

3-way merges 会创建一个新提交 把老的提交合并到一起

# 叫这个名字的原因: 
合并了 源历史, 源之后的历史,新分支的历史三者为一个提交

合并后的历史叫 merge commit

```

![](https://raw.githubusercontent.com/tianran721/img/main/img/20240120113142.png)
7- Merging
8- Fast-forward Merges
9- Three-way Merges
10- Viewing Merged and Unmerged Branches
11- Merge Conflicts
12 - Graphical Merge Tools
13- Aborting a Merge
14- Undoing a Faulty Merge
15- Squash Merging
16- Rebasing
17- Cherry Picking
18- Picking a File from Another Branch
19- Branching in VSCode
20- Branching in GitKraken
1- Introduction
2- Workflows
3- Creating a GitHub Repository
4- Adding Collaborators
5- Cloning a Repository
6- Fetching
7- Pulling
8- Pushing
9- Storing Credentials
10- Sharing Tags
11- Releases
12- Sharing Branches
13- Collaboration Workflow
14- Pull Requests
15- Resolving Conflicts
16- Issues
17- Labels
18- Milestones
19- Contributing to Open-source Projects
20- Keeping a Forked Repository Up to Date
21- Collaboration Using VSCode
22- Collaboration Using GitKraken
1- Introduction
2- Why Rewrite History
3- The Golden Rule of Rewriting History
4- Example of a Bad History
5- Undoing Commits
6- Reverting Commits
7- Recovering Lost Commits
8- Amending the Last Commit
9- Amending an Earlier Commit
10- Dropping Commits
11- Rewording Commit Messages
12- Reordering Commits
13- Squashing Commits
14- Splitting a Commit
15- Rewriting History Using GitKraken
17- Course Wrap Up
