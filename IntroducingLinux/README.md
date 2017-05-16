title: Introducing Linux
speaker: mingchaoyan
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# Introducing Linux
## 分享者：mingchaoyan@gmail.com

[slide]

# 大纲 
---
* Linux 概述 {:&.moveIn}
* Linux 命令初步
* 文件系统
* Vim - 编辑器之神
* SSH - 远程登录
* Q／A

[slide]

# 大纲 
---
* ** Linux 概述 ** {:&.moveIn}

[slide]

# Linux 概述
----
* Unix (/ˈyo͞oniks/) {:&.moveIn}
* ![](/Unix_history-simple.svg.png)

[slide]

# Linux 概述 - Linux 发行版
----

```
* ArchLinux，一个基于KISS（Keep It Simple and Stupid）的滚动更新的操作系统。
* CentOS，从Red Hat发展而来的发行版，由志愿者维护，旨在提供开源的，并与Red Hat 100%兼容的系统。
* Debian，一个强烈信奉自由软件，并由志愿者维护的系统。
* Fedora，是Red Hat的社区版，会经常引入新特性进行测试。
* Gentoo，一个面向高级用户的发行版，所有软件的源代码需要自行编译。
* Kubuntu, 使用KDE桌面的Ubuntu。
* Linux Mint，从Ubuntu派生并与Ubuntu兼容的系统。
* Mandriva，最初为Red Hat的派生版，现在由法国一个同名的公司维护。
* openSUSE，最初由Slackware分离出来，现在由Novell维护。
* Red Hat Enterprise Linux，Fedora的商业版，由Red Hat维护和提供技术支持。
* Ubuntu，一个非常流行的桌面发行版，由Canonical维护。
```
[slide]

# 大纲 
----
* Linux 概述 {:&.moveIn}
* **Linux 命令初步**

[slide]

# Linux 命令初步 - 文件／目录／文本
----
* ls {:&.moveIn}
* mkdir
* grep 

[slide]

# Linux  命令初步 - 进程 / 内存
----
* ps {:&.moveIn}
* top / htop

[slide]

# Linux 命令初步 - 网络工具
----
* ping  {:&.moveIn}
* tracetroute
* netstat
* telnet
* lsof

[slide]

# 大纲 
----
* Linux 概述 {:&.moveIn}
* Linux 命令初步
* **文件系统**

[slide]
# 文件系统 - 常见的文件系统
----
* Windows (Win10) NTFS {:&.moveIn}
* Linux (CentOS7) XFS
```
df -T
```
* macOS (Sierra) HFS+

[slide]

# 文件系统 - 目录树
----
* ![](/linux-file-tree.png)

[slide]
# 文件系统 - 磁盘
----
* 分区(partition) {:&.moveIn}
* 分区表
* Windows 的目录结构属于分区 而 Linux 分区“加载”于目录结构
* ![](/p.png)

[slide]
# 大纲 
----
* Linux 概述 {:&.moveIn}
* Linux 命令初步
* 文件系统
* **Vim - 编辑器之神**

[slide]

# Vim - 编辑器之神
----
* Vi - Vim - gVim {:&.moveIn}
* 让写代码手指移动距离总和最短
* 模式：普通，插入，行末，可视化，可视化块

[slide]

# Vim - 常见模式
----
* 普通 {:&.moveIn}
* 插入 i esc
* 行末 :wq 

[slide]
# 大纲 
----
* Linux 概述 {:&.moveIn}
* Linux 命令初步
* 文件系统
* Vim - 编辑器之神
* **SHH - 远程登录**

[slide]
# SSH - 远程登录 
----
* Secure Shell {:&.moveIn}
* sshd 
* ssh
```
ssh yanmingchao@192.168.83.217 -p 22
```
* ~/.ssh/config
```
Host ci 
User yanmingchao
HostName 192.168.83.217
```
```
ssh ci
```
[slide]
# SSH - 操作
* 建 .ssh 目录 {:&.moveIn}
```
mkdir -p /home/<user-name>/.ssh
```

* 粘贴 key
```
vim /home/<user-name>/.ssh/authorized_keys
```

* 调整权限
```
chmod 700 /home/<user-name>/.ssh
chmod 600 /home/<user-name>/.ssh/authorized_keys
chown -R <user-name>:<group-name> /home/<user-name>/.ssh
```

[slide]

# 推荐
-----
* ![](/Linux1.jpg)  ![](/Linux2.jpg)
* ![](/Unix1.jpg)  ![](/Unix2.jpg)

[slide]
# Q／A

[slide]

# 谢谢!

