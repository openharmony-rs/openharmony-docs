# 应用域名校验错误码
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @hw-xpc-->
<!--Designer: @zhanglin-->
<!--Tester: @sunlin-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 29900001 系统服务内部异常

**错误信息**

An internal error has occurred in the system service.

**错误描述**

当系统服务工作异常时，会报此错误码。

**可能原因**

该错误码表示系统服务工作异常，可能原因如下。

1. 应用域名校验服务无法正常启动。
2. IPC数据读取写入失败。

**处理步骤**

系统服务内部工作异常，请稍后重试，或者重启设备尝试。
