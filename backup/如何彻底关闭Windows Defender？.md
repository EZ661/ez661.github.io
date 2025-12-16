前其实很早之前就想把各种各样的教程收集起来，用我自己的语言二次转述为一个较为完整和成熟的教程。一方面可以防止自己遗忘，或防止遗忘的时候找不到教程原帖，另一方面也可以给大家提供参考，造福人民群众是我一直以来的追求。**为人民服务一定会成功**。

任务管理器中 Windows Defender 的 常驻进程 名为: Antimalware Service Executable
打开 Windows 安全中心，关闭实时保护、云提供的保护、自动提交样本、篡改防护4个选项。
按下 Win+R 输入: msconfig，系统配置页面打开 引导 选项卡。
勾选引导选项中的 安全引导 ，选择 网络（推荐） 或 最小 。
重新启动后，Windows 进入安全模式。
按下 Win+R 输入: gpedit.msc ，启动策略组。
打开 计算机配置-管理模板-Windows组件。
关闭防病毒 - 启用、关闭例程更新 - 启用、实时保护\关闭实时保护 - 启用。
Windows Defender SmartScreen\资源管理器\配置Windows Defender SmartScreen - 禁用
Windows Defender SmartScreen\Microsoft Edge\配置Windows Defender SmartScreen - 禁用
Windows安全中心\Systray\隐藏托盘 - 启用
Windows安全中心\通知\隐藏所有通知 - 启用
按下 Win+R 输入: msconfig，系统配置页面打开 引导 选项卡。
撤销安全引导，重启后进入正常系统。