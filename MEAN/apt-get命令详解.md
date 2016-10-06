# Debian & Ubuntu最实用的apt-get命令详解

## apt-get是Debian、Ubuntu、Linux Mint、elementary OS等Linux发行版的默认软件包管理器。

下面我介绍最最常用的apt-get命令。

```code

$ apt-get update

在安装任何软件之前，我们最好是要更新本地软件包索引（package index）。  
本地软件包索引列出了软件仓库中所有可安装的软件包以及版本信息。

$ sudo apt-get update
sudo的在英语里的意思是switch user and do something． 
在Linux系统上，你需要root权限来安装和卸载软件包。sudo可以临时将你的用户ID切换为root。


apt-get install

apt-get install 是用来安装软件包的。你需要将软件包的名字添加到 apt-get install 之后．  
例如，你可以在Ubuntu系统上安装Chromium浏览器。

sudo apt-get install chromium-browser
有时候apt-get会询问你是否真的要安装软件包。
# 如果你想自动回答**yes**，可以在安装命令中添加 **-y** 选项．

> $ sudo apt-get install -y chromium-browser



在上图中你可以看到，我的Ubuntu系统上已经安装好了Chromium浏览器．

在你用apt-get install命令安装软件包之前，你需要知道这个软件包在软件仓库中的名称．  
这看起来有点麻烦．当你熟悉之后，你会感到非常方便．尤其是当你SSH远程管理Linux服务器的时候．

apt-get首先会从软件仓库中下载deb安装包，这些deb安装在/var/cache/apt/archives目录下．  
下载后，apt-get会自动安装软件包

一条命令安装多个软件包

apt-get install 可以一次性安装多个软件包，比如

$ sudo apt-get install wireshark nmap aircrack-ng



apt-get upgrade

apt-get upgrade命令用来升级系统上可以升级的软件包．

sudo apt-get upgrade

apt-get 会告诉你哪些软件包会升级．并且询问你是否真的需要升级这些软件包．你可以在命令中添加 -y 选项来自动回答yes．

sudo apt-get -y upgrade
apt-get remove

这条命令用来删除系统上的软件包，比如，删除Firefox

sudo apt-get remove firefox
它不会删除软件包的配置文件．

apt-get purge

这条命令可以用来删除软件包及其配置文件．

sudo apt-get purge firefox

apt-get clean

当apt-get安装或升级软件包时，它会将deb安装包下载到文件系统的/var/cache/apt/archives目录下．  
软件包安装完成后，这些deb安装包基本上就没有什么用处了．apt-get clean命令可以帮你删除这些deb安装包．

你可以使用下面的命令查看/var/cache/apt/archives目录下deb安装包的大小．

du -sh /var/cache/apt/archives

apt-get autoclean

apt-get autoclean也可以用来删除/var/cache/apt/archives目录下的deb安装包．  
但它只删除那些已经不能从软件仓库中下载的deb安装包．  
这就是说，Debian或Ubuntu已经不维护那些软件包了，或者那些软件包有了一个新的名字．

apt-get autoremove

这条命令用来删除不需要的依赖软件包．

apt-get dist-upgrade

这条命令可能会让很多人感到困惑．  
在Debian系统上，你用这条命令升级系统版本，比如从Debian 7升级到Debian 8．  
但是在Ubuntu系统上，这条命令只会升级Linux内核以及之前没有被升级的软件包．  
升级Ubuntu的版本你需要用到do-release-upgrade命令．

附：手动安装Deb软件包

dpkg -i

如果你从网站上下载了一个deb软件包，那么你需要dpkg工具来安装这个deb包．  
例如，你可以下载WPS linux版．然后，在终端里将当前工作目录切换到下载目录，再输入下面的命令安装WPS  Linux版．

sudo dpkg -i wps-office*.deb
gdebi

dpkg的一个缺点是它不能解决依赖关系．你必须手动安装依赖包．  
而gdebi可以帮助我们自动安装依赖包．输入下面的命令安装gdebi

sudo apt-get install gdebi
它的命令语法如下：

sudo gdebi <package.deb>



OpenGL超级宝典；OpenGL超级圣经 OpenGL Super Bible:



``` 


