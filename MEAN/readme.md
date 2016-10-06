# 在Ubuntu 15.10搭建MEAN开发环境

在Ubuntu 15.10搭建MEAN开发环境

本文主要讲述如何在Ubuntu 15.10系统上搭建MEAN开发环境。

1、安装Node.js和使用nvm安装npm
nvm是一个简单的Bash脚本，可用于在同一台主机上安装和维护不同的Node.js版本。执行命令：

# wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
此脚本会克隆nvm仓库到~/.nvm，并配置环境变量（在~/.bash_profile文件或~/.zshrc文件或~/.profile中配置）

要下载、编译、安装最新的Node.js，可以简单的执行命令：

# nvm install 4.2.2
现在，可以确定使用这个版本的Node.js，执行命令：

# nvm use 4.2.2
使用nvm，还可以安装其它版本的Node.js，比如最新的非稳定版，又或者是比较老的版本，只需使用nvm命令，并指定Node.js的版本进行安装即可。

对于Node.js的开发，还需要npm包管理器，MEAN全栈开发也需要它。Node.js内置了npm，因此无需单独安装npm。如果想使用最新版本的npm，可以这样：

# npm install -g npm
上面的命令会安装最新版本的npm。搭建Node.js环境的所有步骤如上所述。

2、安装MongoDB
首先，需要导入MongoDB的公钥GPG，使用命令：

# sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
然后，可以从Debian wheezy软件仓库获得MongoDB软件，使用命令：

# echo "deb http://repo.mongodb.org/apt/debian wheezy/mongodb-org/3.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
接着，升级本地的软件包：

# sudo apt-get update
最后，使用命令安装最新的、稳定版的MongoDB：

# sudo apt-get install -y mongodb-org
此时，可以使用sudo service mongodb start命令来启动MongoDB服务。如果提示失败，可以使用以下的命令进行修复：

创建/data/db目录，并打开MongoDB的配置文件：

# sudo mkdir -p /data/db
# sudo gedi
修改内容dbpath=/var/lib/mongodb改成dbpath=/data/db，并保存文件。

# sudo chown -R mongodb:mongodb /data/db
现在，可以再次启动MongoDB服务了。

# sudo service mongod start
要检查MongoDB服务的状态，使用命令：

# sudo systemctl status mongod
搭建MongoDB环境使用如上的步骤就足够了，接下来开始搭建MEAN环境。

3、安装MEAN
首先，需要安装Bower。Bower是一个包管理器，可以管理前端的各种库包，比如Angular.js、BootStrap、jQuery库等。使用如下命令安装Bower：

# npm install -g bower
接着，还需要安装Grunt，Grunt是一个任务运行器，可以把部署过程自动化。执行命令：

# npm install -g grunt-cli
这会全局安装grunt命令行工具。

要下载MEAN，可以从Git源码仓库中克隆它到项目目录下：

# git clone https://github.com/meanjs/mean.git meanjs
现在，打开mean文件夹，在其父目录下执行命令：

# npm install
这样会安装项目所需的所有依赖，这些依赖在package.json配置文件中有定义。

最后，运行grunt：

# grunt
这会自动打开一个新页面，显示MEAN.JS欢迎页面：

注意： 
* 在运行grunt后，有可能会出现错误页，提示”couldn’t start MongoDB on default port 27017.“（即提示不能访问MongoDB默认的27017端口）。此时，需要使用管理员权限开放27017端口。 
* MEAN全栈开发是很棒的，现在可以开始了。
