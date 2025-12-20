首先你要租一个服务器， 你总不可能在自己的电脑上运行一个机器人24小时吧？所以租一个服务器是我们最好的选择。租了服务器之后，往往只给提供一个盘的空间，比如你买了50G的硬盘空间的服务器，可能这50GB全部给你放到C盘，但是我们的机器人如果运行在系统盘经常会遇到权限和存储方面的各种问题，所以我们要做的第一件事就是在计算机管理中，把C盘压缩出个10-20G，然后新建卷一个D盘出来，在D盘下进行操作，**我会告诉你每一步该做什么，以及为什么这么做。**也就是说我们的第一件事就是，以下

- 所有操作均在非系统盘进行，如果没有就新建。所有的文件建议在本地下载，最后打包上传到服务器。

然后我们搭建环境，安装的每个工具，依赖，没有先后顺序要求，随便。我这里为了美观，一条一条写出来，实际上没有顺序要求的。

- 前往https://github.com/NapNeko/NapCatQQ/releases 下载VC运行库

- 前往https://git-scm.com/下载最新版的git

后面我们git库用

- 前往https://github.com/NapNeko/NapCatQQ/releases 下载最新版的NapCat.Shell.zip

这是NapCat的主程序，肯定要下载，因为没有QQNT本体所以下面再下载QQNT。

- 前往https://im.qq.com/pcqq/index.shtml 下载最新版QQNT

这里是下载QQNT本体，当然需要，无需解释。

- 前往https://github.com/coreybutler/nvm-windows/releases 下载最新版的nvm-setup.exe

这是下载NVM，NVM是用来管理Node.js版本用的，Yunzai-Miao需要Node.js环境。

- 前往https://www.microsoft.com/zh-cn/edge/download 下载最新版的Edge浏览器

因为Yunzai-Miao需要Chromium/Edge的环境，也就是说下谷歌浏览器也可以，看你自己。

- 前往https://github.com/redis-windows/redis-windows/releases 下载Redis-8.4.0-Windows-x64-msys2-with-Service.zip

这是Redis，同样是Yunzai-Miao需要的环境。
接下来是把上面的东西通通安装，这里的安装有顺序要求的，按照顺序来。

- 安装VC运行库，安装Edge浏览器，安装QQNT，安装NVM，安装Redis，解压NapCat。

- 在D盘新建一个文件夹，名字不要有中文，然后我们用cmd来开始安装Yunzai-Miao，cmd记得关闭快速编辑模式

- 先获得Yunzai`git clone --depth=1 https://gitee.com/yoimiya-kokomi/Miao-Yunzai.git`

- 然后进入Yunzai的目录获得对应的插件`git clone --depth=1 https://gitcode.com/TimeRainStarSky/miao-plugin.git plugins/miao-plugin`
