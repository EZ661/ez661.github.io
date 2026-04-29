### Windows Defender的进程
在任务管理器中 Windows Defender 的 常驻进程 名为: Antimalware Service Executable
### 在正常系统模式中关闭
打开 Windows 安全中心，关闭实时保护、云提供的保护、自动提交样本、篡改防护4个选项。
### 切换到安全模式
按下 Win+R 输入: msconfig，系统配置页面打开 引导 选项卡。
勾选引导选项中的 安全引导 ，选择 网络（推荐） 或 最小 。
重新启动后，Windows 进入安全模式。
### 关闭策略组中的Defender及其附属
按下 Win+R 输入: gpedit.msc ，启动策略组。
打开 计算机配置-管理模板-Windows组件。
关闭防病毒 - 启用、关闭例程更新 - 启用、实时保护\关闭实时保护 - 启用。
Windows Defender SmartScreen\资源管理器\配置Windows Defender SmartScreen - 禁用
Windows Defender SmartScreen\Microsoft Edge\配置Windows Defender SmartScreen - 禁用
Windows安全中心\Systray\隐藏托盘 - 启用
Windows安全中心\通知\隐藏所有通知 - 启用
### 回到正常的系统
按下 Win+R 输入: msconfig，系统配置页面打开 引导 选项卡。
撤销安全引导，重启后进入正常系统。看到右下角无托盘图标即为成功。