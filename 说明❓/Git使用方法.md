
# 仓库初始化
## 安装Git

## 创建GitHub仓库

不要勾选README

创建完成后，复制仓库的SSH地址。
[Viola-2003/Obsidian-Research: 个人知识库](https://github.com/Viola-2003/Obsidian-Research)

## 生成SSH Key
[保姆教程系列：生成 SSH Key 并配置连接远程仓库 - 南国以南i - 博客园](https://www.cnblogs.com/bgyb/p/18889532#-%E7%AC%AC-1-%E6%AD%A5%E6%A3%80%E6%9F%A5%E6%98%AF%E5%90%A6%E5%B7%B2%E6%9C%89-ssh-key)
## 初始化

打开git Bash
```
//切换到目标路径
cd /d/aNote/Research  

//初始化git项目
git init

//添加远程仓库
git remote add origin git@github.com:Viola-2003/Obsidian-Research.git

```

在Obsidian仓库根目录创建一个.gitignore文件，排除不想同步的文件。如：
```
.obsidian/app.json
.obsidian/appearance.json 
.obsidian/canvas.json
.obsidian/graph.json
.obsidian/workspace.json
.trash/
```

## 提交初始文件

```
//添加所有文件到Git
git add .

//提交更改
git commit -m "Initial commit"  

//重命名本地仓库
git branch -m master main

//推送到GitHub
git push -u origin main

//如果推送失败，试一下能否连接，若成功，再次推送
ssh -T git@github.com
```
如果正在使用代理服务器，可能导致连接失败。如果使用HTTPS连接，则必须要用代理服务器，但用代理服务器会连接不上。所以用SSH，记得回国。

# 其它设备的同步

## 安装Git
看第1步~第6步。第7步不看。
[【2025年最新版】Git安装及环境配置超详细教程（以win11为例子）_git安装及配置教程-CSDN博客](https://blog.csdn.net/Little_Carter/article/details/155110165)

## 配置SSH Key
[保姆教程系列：生成 SSH Key 并配置连接远程仓库 - 南国以南i - 博客园](https://www.cnblogs.com/bgyb/p/18889532#-%E7%AC%AC-1-%E6%AD%A5%E6%A3%80%E6%9F%A5%E6%98%AF%E5%90%A6%E5%B7%B2%E6%9C%89-ssh-key)
（其中第8步不看）
## 初始化

```
//前往目标文件夹
cd /f/Test         

//克隆（记得先回国，否则SSH连接不上）
git clone git@github.com:Viola-2003/Obsidian-Research.git

//接着用Obsidian打开仓库：Obsidian-Research（位于f/Test/）
```