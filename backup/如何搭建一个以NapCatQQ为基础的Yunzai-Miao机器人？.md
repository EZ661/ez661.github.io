### 前言
首先你要租一个服务器， 你总不可能在自己的电脑上运行一个机器人24小时吧？所以租一个服务器是我们最好的选择。租了服务器之后，往往只给提供一个盘的空间，比如你买了50G的硬盘空间的服务器，可能这50GB全部给你放到C盘，但是我们的机器人如果运行在系统盘经常会遇到权限和存储方面的各种问题，所以我们要做的第一件事就是在计算机管理中

- 把C盘压缩出个10-20G，然后新建卷一个D盘出来，在D盘下进行操作

我会告诉你每一步该做什么，以及为什么这么做。以下所有操作均在非系统盘进行，如果没有就新建。所有的文件建议在本地下载，或者直接在有恰当网络环境的服务器上直接进行下载，最后打包上传到服务器。然后我们搭建环境，安装的每个工具，依赖，没有先后顺序要求，随便。我这里为了美观，一条一条写出来，实际上没有顺序要求的。

- 前往https://github.com/NapNeko/NapCatQQ/releases 下载VC运行库

这是给QQNT提供环境，即VC运行库

- 前往https://git-scm.com/ 下载最新版的git

后面我们git库用

- 前往https://github.com/NapNeko/NapCatQQ/releases 下载最新版的NapCat.Shell.zip

这是NapCat的主程序，肯定要下载，因为没有QQNT本体所以下面再下载QQNT。

- 前往https://github.com/NapNeko/NapCatQQ/releases 下载最新版QQNT

这里是下载QQNT本体，当然需要，无需解释。

- 前往https://github.com/coreybutler/nvm-windows/releases 下载最新版的nvm-setup.exe

这是下载NVM，NVM是用来管理Node.js版本用的，Yunzai-Miao需要Node.js环境。

- 前往https://www.microsoft.com/zh-cn/edge/download 下载最新版的Edge浏览器

因为Yunzai-Miao需要Chromium/Edge的环境，也就是说下谷歌浏览器也可以，看你自己。

- 前往https://github.com/redis-windows/redis-windows/releases 下载Redis-8.4.0-Windows-x64-msys2-with-Service.zip

这是Redis，同样是Yunzai-Miao需要的环境。
接下来是把上面的东西通通安装，这里的安装有顺序要求的，按照顺序来。

- 安装VC运行库，安装Edge浏览器，安装QQNT，安装QQNT时不要勾选自动更新，安装NVM，安装Redis，解压NapCat，安装Git，重启电脑。
- 安装Redis时，请运行install_redis_service

- 在D盘新建一个文件夹，名字不要有中文，然后我们用powershell来开始安装Yunzai-Miao，powershell记得关闭快速编辑模式

- 先获得Yunzai

```
git clone --depth=1 https://gitee.com/yoimiya-kokomi/Miao-Yunzai.git
```

- 然后进入Yunzai的目录获得对应的插件

```
git clone --depth=1 https://gitcode.com/TimeRainStarSky/miao-plugin.git plugins/miao-plugin
```

- 安装node.js

```
nvm install lts
nvm use lts
```

- 安装pnpm，如果你遇到了 PowerShell 的权限问题，请修改 PowerShell 执行策略，见第二行命令

```
npm install pnpm -g
```

```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

> RemoteSigned 策略允许运行本地脚本，但从互联网下载的脚本需要签名，是比较平衡的安全设置。

- 安装Miaozai依赖

```
pnpm install -P
```

- 运行Miaozai-Yunzai

```
npm run app
```

运行完让你输入信息，如机器人QQ和主人QQ，你只需要一直回车下一步即可，输入完这些参数，Miaozai会自动生成一些文件，然后我们关掉Miaozai即可。
我们接下来配置NapCat。
找到前面解压的NapCat.Shell文件夹，同样使用PowerShell运行launcher-win10.bat，当然，根据你系统的版本选择运行，即输入
```
./launcher-win10.bat
```

然后在PowerShell界面找到形如http://127.0.0.1:6099/webui?token=XXX 的字段，复制粘贴到浏览器地址栏，这是NapCat的内网管理后台地址，token的值为首次登录的密码。
登录后台后首先修改密码。
在系统配置-修改密码中。

打开网络配置-上方-新建-新建WS服务器
打开启用，名称随意。token随意，并记住或保存

接下来回到Miaozai
安装Guoba插件，即锅巴插件，这是一个用来管理Miaozai后台的插件，如管理其他插件的配置或机器人的配置，总之这是一个必装插件。

```
git clone --depth=1 https://gitee.com/guoba-yunzai/guoba-plugin.git ./plugins/Guoba-Plugin/
```

然后安装锅巴的依赖

```
pnpm install --filter=guoba-plugin
```

> 原文：如果你不是通过pnpm安装的云崽，那么请不要使用此方式
> 如果你是使用pnpm安装的云崽，那么只需要在云崽根目录下运行此命令即可

我们是pnpm安装的云崽，所以可以使用以上命令。

然后我们安装NapCat适配器，有了这个我们的Miaozai可以使用NapCat。
```
git clone --depth=1 https://gitee.com/qiannqq/napcat-adapter.git ./plugins/napcat-adapter
```
安装依赖
```
pnpm install --filter=napcat-adapter
```
打开.\config\config\bot.yaml，将跳过ICQQ的值改为true
然后再次运行云崽。
```
npm run app
```

然后应该会有两个错误，一个是没有配置NapCat适配器的AccessToken，一个是缺少依赖，我们一个一个来，先解决第一个。
打开http://127.0.0.1:50831/ 这是锅巴的后台，用来配置NapCat适配器
然后获取验证码，到Shell中找到验证码并输入。
在左侧，插件配置中，找到NapCat适配器，在右侧配置你先前输入的Token。
然后直接关闭Miaozai，我们来解决第二个问题，再次运行PowerShell。输入以下
```
pnpm i
```
来安装提示缺少的依赖。
再次运行Miaozai
```
npm run app
```
如果你看见了机器人给你发的状态信息，恭喜你，大功告成！

以下是可选的内容或插件

安装三角洲行动插件
```
git clone https://gitee.com/Dnyo666/delta-force-plugin.git ./plugins/delta-force-plugin
```
安装依赖
```
pnpm install --filter=delta-force-plugin
```
此插件需要自行配置相关内容

安装R插件（解析B站抖音视频百度贴吧等）
```
git clone https://gitee.com/kyrzy0416/rconsole-plugin.git ./plugins/rconsole-plugin/
```
安装依赖
```
pnpm i --filter=rconsole-plugin
```
此插件需要自行配置相关内容，另外需要ffmpeg相关库
前往https://www.gyan.dev/ffmpeg/builds/下载
找到release builds
下载ffmpeg-release-full.7z
此库需要手动配置系统环境变量以调用
具体方法如下，此为教程帖
https://blog.csdn.net/Natsuago/article/details/143231558

此外R插件的抖音视频解析需要配置抖音cookies
具体方法如下
[R插件Q&A文档](https://zhiyu1998.github.io/rconsole-plugin/posts/QA%E5%AE%98%E6%96%B9%E8%A7%A3%E7%AD%94.html)

完结！