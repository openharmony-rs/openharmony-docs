# 云盘管理错误码（系统接口错误码）
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @zhuangzhuang-->
<!--Designer: @wang_zhangjun; @zhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 34400003 IPC通信失败

**错误信息**

IPC communication failed

**错误描述**

IPC通信失败。

**可能原因**

调用服务不存在。

**处理步骤**

检查服务是否启动。

## 34400014 系统内部错误

**错误信息**

Temporary failure, Retry is recommended (e.g., network issues).

**错误描述**

内部错误。

**可能原因**

网络通信异常，数据写入数据库失败。

**处理步骤**

由当前应用进行重试。

## 34400015 当前设备不允许使用云盘功能

**错误信息**

Cloud disk not allowed on this device.

**错误描述**

当前设备不允许使用云盘功能。

**可能原因**

当前设备不允许使用云盘功能。

**处理步骤**

三方云盘应用弹框提示用户“当前设备不允许使用云盘功能”。
