## 查看设置的环境变量
- `set` 命令查看

## Windows 环境变量
|变量|解释|
|-|-|
|`%ALLUSERSPROFILE%`|返回所有“用户配置文件”的位置。|
|%APPDATA% | 返回默认情况下应用程序存储数据的位置。
|%CD% | 返回当前目录字符串。
|%CMDCMDLINE% | 返回用来启动当前的 cmd.exe 的准确命令行。
|%CMDEXTVERSION% | 返回当前的“命令处理程序扩展”的版本号。
|%COMPUTERNAME% | 返回计算机的名称。
|%COMSPEC% | 返回命令行解释器可执行程序的准确路径。
|%DATE% | 返回当前日期。使用与 date /t 命令相同的格式。由 cmd.exe 生成。有关 date 命令的详细信息，请参阅 Date。
|%ERRORLEVEL% | 返回最近使用过的命令的错误代码。通常用非零值表示错误。
|%HOMEDRIVE% | 返回连接到用户主目录的本地工作站驱动器号。基于主目录值的设置。用户主目录是在“本地用户和组”中指定的。
|%HOMEPATH% | 返回用户主目录的完整路径。基于主目录值的设置。用户主目录是在“本地用户和组”中指定的。
|%HOMESHARE% | 返回用户的共享主目录的网络路径。基于主目录值的设置。用户主目录是在“本地用户和组”中指定的。
|%LOGONSEVER% | 返回验证当前登录会话的域控制器的名称。
|%NUMBER_OF_PROCESSORS% | 指定安装在计算机上的处理器的数目。
|%OS% | 返回操作系统的名称。Windows 现在将操作系统显示为 Windows_NT。
|%PATH% | 指定可执行文件的搜索路径。
|%PATHEXT% | 返回操作系统认为可执行的文件扩展名的列表。
|%PROCESSOR_ARCHITECTURE% | 返回处理器的芯片体系结构。值: x86，IA64。
|%PROCESSOR_IDENTFIER% | 返回处理器说明。
|%PROCESSOR_LEVEL% | 返回计算机上安装的处理器的型号。
|%PROCESSOR_LEVEL% | 返回处理器的版本号。
|%PROMPT% | 返回当前解释程序的命令提示符设置。由 cmd.exe 生成。
|%RANDOM% | 返回 0 到 32767 之间的任意十进制数字。由 cmd.exe 生成。
|%SYSTEMDRIVE% | 返回包含 Windows 根目录（即系统根目录）的驱动器。
|%SYSTEMROOT% | 返回 Windows 根目录的位置。
|%TEMP% | 返回对当前登录用户可用的应用程序所使用的默认临时目录。有些应用程序需要 TEMP，而其它应用程序则需要 TMP。
|%TMP% | 同上
|%TIME% | 返回当前时间。使用与 time /t 命令相同的格式。由 cmd.exe 生成。有关 time 命令的详细信息，请参阅 Time。
|%USERDOMAIN% | 返回包含用户帐户的域的名称。
|%USERNAME% | 返回当前登录的用户的名称。
|%UserPrefix% | 返回当前用户的配置文件的位置。
|%WINDIR% | 返回操作系统目录的位置。