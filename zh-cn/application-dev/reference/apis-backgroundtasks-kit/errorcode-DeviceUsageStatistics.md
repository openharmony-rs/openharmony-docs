# DeviceUsageStatistics错误码
<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @fenglili18-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 10000001 内存操作失败

**错误信息**

Memory operation failed.

**错误描述**

内存操作失败。

**可能原因**

该错误码表示系统服务工作异常，可能原因是内存不足导致创建对象失败。

**处理步骤**

请检查内存是否泄漏。

## 10000002 IPC parcel write failed

**错误信息**

Parcel operation failed. Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory.

**错误描述**

进程间通信的时候，写入数据对象失败。

**可能原因**

1. 参数无效。
2. 申请内存失败。

**处理步骤**

1. 请检查参数是否合法，例如字符串是否超长等。
2. 请重试。

## 10000003 系统服务操作失败

**错误信息**

Failed to get system ability manager.

**错误描述**

客户端进程请求服务进程时，获取系统服务操作失败。

**可能原因**

依赖的服务进程出现问题。

**处理步骤**

系统服务内部工作异常，请稍后重试，或者重启设备尝试。

## 10000004 通信失败

**错误信息**

Failed to access the device usage service.

**错误描述**

进程间通信的时候，通信失败。

**可能原因**

系统服务异常或者通信数据异常。

**处理步骤**

系统服务内部工作异常，请稍后重试，或者重启设备尝试。

## 10000005 应用未安装

**错误信息**

The application is not installed.

**错误描述**

应用未安装。

**可能原因**

应用未安装或者已经卸载。

**处理步骤**

操作应用信息时请先检查应用是否存在。

## 10000006 获取应用信息失败

**错误信息**

Failed to get the application information.

**错误描述**

客户端进程获取服务中相关应用信息失败。

**可能原因**

1. beginTime或者endTime输入不合法。
2. 应用未安装或者已经被卸载了。
3. intervalType输入不合法。

**处理步骤**

请检查入参合法性以及应用是否存在。

## 10000007 时间操作失败

**错误信息**

Failed to get the system time.

**错误描述**

系统服务获取系统时间或者实际时间操作失败。

**可能原因**

系统异常。

**处理步骤**

系统服务内部工作异常，请稍后重试，或者重启设备尝试。

## 10100001 应用分组信息操作重复

**错误信息**

Repeated operation on the application group.

**错误描述**

应用分组操作失败。

**可能原因**

重复设置应用分组、重复注册分组变化监听、或重复取消分组变化监听。

**处理步骤**

请勿重复设置应用分组、注册监听和取消监听。

## 10100002 获取应用分组信息失败

**错误信息**

Failed to get the application group information.

**错误描述**

客户端进程获取应用分组信息失败，该信息在数据库中不存在。

**可能原因**

1. 应用输入bundleName错误。
2. 应用可能没有安装或者已经卸载。

**处理步骤**

请检查入参bundleName的合法性和应用是否存在。

