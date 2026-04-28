### 注册账号
1. 前往简幻欢的官网 simpfun.cn [点我跳转](https://www.simpfun.cn/) 注册一个简幻欢账号，根据官网指引完成注册。
### 新建实例
2. 进入简幻欢官网，点击进入控制台，然后新建实例，选择基础镜像，实例类别选择Terraria，服务端选择TModLoader，版本选择最新版本，最后确认创建。
### 提取TML服务器文件
3. 打开Steam，下载游戏TModLoader。在Steam左侧游戏列表右键-管理-浏览本地文件，运行一次start-tModLoaderServer.bat文件，第一个提示输入n，到选择世界的步骤时关闭程序，然后在目录中全选所有的文件，右键压缩为一个压缩包，建议压缩为7z。
### 删除简幻欢的原服务端并上传新的服务端
4. 回到简幻欢刚刚新建的实例，点击文件，全选所有文件删除，简幻欢会保留一个启动脚本，然后将刚刚压缩好的压缩包上传到简幻欢。勾选上传好的压缩包，点击右下角的工具箱中的解压。
### 修改启动脚本内容
5. 找到简幻欢文件列表中的start.sh文件，点击这个文件打开编辑，在`cd "$(dirname "$0")" || exit`之后增加一行代码 `mise use -g dotnet@8.0`，然后保存文件。
### 打包本地模组为整合包
6. 在tml中将自己要玩的即上传到服务器的模组全部启用，确认配置好后，在模组管理页面点击将已启用模组保存为模组整合包，然后点击导出整合包，然后打开创建好的模组整合包的文件夹，切换到Mods和Modconfigs两个文件夹的目录，将这两个文件夹打包压缩，建议压缩为7z。
### 修改启动项指定模组及配置文件存放目录
7. 打包之后再上传到启动脚本所在的目录并解压，会在当前目录产生两个目录即Mods和Modconfigs文件夹，打开start.sh文件编辑，删除所有以`launch_args="-server"`开头的代码，并最终新增一行代码`launch_args="-server -config server.properties -modpath /home/container/Mods -tmlsavedirectory /home/container"`，此代码将模组路径指定至刚刚我们解压的两个目录，修改后的sh脚本的内容为
```
#!/usr/bin/env bash
cd "$(dirname "$0")" || exit
mise use -g dotnet@8.0
launch_args="-server"
launch_args="-server -config server.properties -modpath /home/container/Mods -tmlsavedirectory /home/container"
dotnet tModLoader.dll $launch_args
```
请自行对照复制粘贴修改。
### 大功告成
8. 返回到简幻欢的终端页面，点击右上角的启动服务器即可运行你的定制模组服了。