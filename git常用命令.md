# 一. 初始化仓库

```
$ mkdir git-study && cd git-study
$ git init
```

# 二. 配置指令，全局指令

```
$ git config user.name GanZhengHui
$ git config user.email 2033148903@qq.com
```

## 全局配置

```
$ git config --global user.name GanZhengHui
$ git config --global user.email 2033148903@qq.com
```

# 三. git工作大致原理图

![image-20230824231545353](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230824231545353.png)

# 四. 状态

## 查看当前状态

```
git status
```

## 将a.txt文件添加到缓存区

```
git add a.txt
```

## 将a.txt从缓存区移除

```
 git rm --cached a.txt
```

## 从缓存区提交到存储区(即本地仓库)

```
$ git commit -m 新增文件 //m表示信息 新增文件是提交信息
```

## 查看最近日志

```
$ git log --oneline //只显示一行
```

## 从本地仓库恢复误删的文件

```
$ git restore 文件名
```

## 本地仓库里的也没了，可用reset或者revert

```
$ git reset --hard 版本号
$ git revert 版本号
```

# 五. 分支操作

```
$ git branch user  //创建分支user，前提是原来master必须有

$ git checkout user  //切换当前分支，切到user

$ git checkout -b user  //前面两个命令的合并写法，创建user分支并切换到改分支

$ git branch -v  //查看所有分支

$ git branch -d user  //删除user分支
```

# 六. 合并操作

```
$ git merge order  //要在master分支下操作，将order分支添加进主分支
```

# 七. 添加标签

```
$ git tag //查看所有标签

$ git tag 标签名字 版本号  //给某个版本添加标签

$ git tag -d 标签名称  //删除标签名
```

# 八. 远程仓库操作

```
$ git push orign  //推送到远程仓库

$ git pull orign  //将远程仓库拉取到本地仓库
```

