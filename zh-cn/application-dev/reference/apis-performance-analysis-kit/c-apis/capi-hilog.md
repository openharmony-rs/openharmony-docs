# HiLog

## 概述

实现日志打印功能。使用这些接口可以输出指定日志类型、业务领域、日志标签和日志级别的日志。

**起始版本：** 8
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [log.h](capi-log-h.md) | 定义HiLog模块的日志功能。在输出日志之前，先定义日志所属业务领域、日志标签，然后按照日志类型、日志级别选择对应接口，并指定隐私标识符。 <br> <ul><li>业务领域： 用于标识服务的子系统或模块，其值为0x0到0xFFFF的十六进制整数。 <br> <li>日志标签：字符串常量，用于标识调用所在的类或者业务。</li> <br> <li>日志级别：<b>DEBUG</b>、<b>INFO</b>、<b>WARN</b>、<b>ERROR</b>和<b>FATAL</b></li> <br> <li>参数格式：以%字符开头的printf格式字符串，包括格式说明符和可变参数。</li> <br> <li>隐私参数标识：在每个参数中%字符和格式说明符之间增加{public}、{private}标识。请注意，每个参数都有一个隐私标识符。如果未添加隐私标识符，缺省为隐私。</li></ul> <br> 示例代码：<br> 定义业务领域和日志标签：<br>     #include <hilog/log.h><br>     #define LOG_DOMAIN 0x0201<br>     #define LOG_TAG "MY_TAG"<br> 输出日志：<br>     HILOG_WARN([LOG_APP](capi-log-h.md#logtype), "Failed to visit %{private}s, reason:%{public}d.", url, errno);<br> 输出结果：<br>     05-06 15:01:06.870 1051 1051 W 0201/MY_TAG: Failed to visit <private>, reason:503.<br> |
