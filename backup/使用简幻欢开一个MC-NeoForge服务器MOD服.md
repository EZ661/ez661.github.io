访问https://neoforged.net/进入neoforged官网
在NeoForge installer files栏选择游戏版本和NeoForge版本
游戏版本选择MOD支持的版本
NeoForge选择最新的版本即可（或者MOD支持的版本）
然后点击Download Installer（需要Java环境）
在国内环境下（也许是Watt Toolkit加速器加速GitHub的环境下）
该安装器可以正常使用安装
目录选择一个空的临时目录
安装时选择伺服器（即服务器）
此时你获得了一个MC-NeoForge你需要的版本的服务器文件
把他压缩起来上传到简幻欢（记得提前清空简幻欢的所有文件）
修改启动脚本run.sh的内容
主要修改以下几点：修改开头的解释器为 #!/bin/bash java命令开头的绝对路径 将 user_jvm_args.txt 预置指令设置为 -Xms1024M -Xmx${SERVER_MEMORY}M 简幻欢自带的指定内存堆 以及添加-server指定模式 末尾指定对应版本 @libraries/net/neoforged/neoforge/21.1.228/unix_args.txt "$@"
最终的版本如下（并不完全是，根据情况变化参考）
```
#!/bin/bash
# Forge requires a configured set of both JVM and program arguments.
# Add custom JVM arguments to the user_jvm_args.txt
# Add custom program arguments {such as nogui} to this file in the next line before the "$@" or
#  pass them to this script directly
"/usr/bin/jdk/jdk-21.0.2/bin/java" -Xms1024M -Xmx${SERVER_MEMORY}M -server @libraries/net/neoforged/neoforge/21.1.228/unix_args.txt "$@"
```
然后将这个内容修改至简幻欢的run.sh文件
在整个服务器文件的根目录将所有文件压缩为一个压缩包
再将这个压缩包上传至服务器解压
然后回到简幻欢的终端启动一次服务器
服务器终端提示需要同意一个协议
将此文件协议的false改为true
再次启动服务器
等待启动后，就大功告成
MOD全部上传至mods文件夹即可