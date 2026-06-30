# 维测日志错误码

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @BruceZong-->
<!--Designer: @gcw_qzKyUhyU-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 21300001 指定文件不存在

**错误信息**

The specified file does not exist.

**错误描述**

在调用日志文件的拷贝、移动或删除接口进行文件操作时，指定的日志文件不存在。

**可能原因**

- 传入的文件名称不正确。

- 传入的文件名在设备存储中不存在。

**处理步骤**

- 检查传入的文件名称是否正确，包括文件名拼写以及路径格式。
- 确认文件在设备存储中是否存在，检查文件路径和日志目录配置是否正确。
