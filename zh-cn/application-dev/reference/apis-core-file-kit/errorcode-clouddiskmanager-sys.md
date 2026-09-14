# 云盘管理错误码（系统接口错误码）
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 34400001 输入参数无效

**错误信息**

Invalid argument.

**错误描述**

输入参数无效。

**可能原因**

文件路径为空、不是绝对路径、包含非法路径段（如“..”或“.”），或枚举参数取值不在允许范围内。

**处理步骤**

检查并修正入参后重试。

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

Cloud disk is not allowed on this device.

**错误描述**

当前设备不允许使用云盘功能。

**可能原因**

当前设备不允许使用云盘功能。

**处理步骤**

三方云盘应用弹框提示用户“当前设备不允许使用云盘功能”。

## 34400017 目标路径不是占位符文件

**错误信息**

The target path is not a placeholder file.

**错误描述**

目标路径不是占位符文件。

**可能原因**

对普通文件（未标记为占位符的文件）调用水合或脱水接口。

**处理步骤**

确认目标文件为三方云盘应用创建的占位符文件后再调用。

## 34400019 水合任务已在进行中

**错误信息**

Hydration in progress.

**错误描述**

目标文件已存在进行中的水合任务。

**可能原因**

同一文件的水合任务尚未完成或未取消时再次发起水合，或水合进行中调用脱水接口。

**处理步骤**

等待水合完成，或先将水合任务取消（调用hydratePlaceholder时callbackType取CANCEL_FETCH_DATA）后再操作。

## 34400021 回调表未注册

**错误信息**

The callback table is not registered.

**错误描述**

云盘应用回调表未注册。

**可能原因**

目标路径不在任何已注册的同步根目录范围内，或目标路径所属同步根对应的三方云盘应用未注册回调表。

**处理步骤**

确认目标路径位于已注册的同步根目录范围内，且对应的三方云盘应用已完成回调表注册。

## 34400028 占位符文件未完全水合

**错误信息**

The placeholder file is not fully hydrated.

**错误描述**

占位符文件未完全水合。

**可能原因**

对处于未水合或部分水合状态的占位符文件调用脱水接口。

**处理步骤**

先调用hydratePlaceholder完成水合后再执行脱水。

## 34400029 云盘应用拒绝脱水

**错误信息**

The application denied placeholder dehydration.

**错误描述**

三方云盘应用拒绝了脱水授权。

**可能原因**

脱水前系统向三方云盘应用发起脱水授权请求，云盘应用返回不允许脱水（如文件正在被云端使用）。

**处理步骤**

尊重云盘应用的授权结果，暂不执行脱水操作。

## 34400031 占位符文件已完全水合

**错误信息**

The placeholder file is already fully hydrated.

**错误描述**

占位符文件已完全水合，无需再次水合。

**可能原因**

对已完全水合的占位符文件再次发起水合。

**处理步骤**

无需处理，文件内容已在本地。

## 34400032 无进行中的水合任务

**错误信息**

No hydration task is in progress for the target file.

**错误描述**

目标文件不存在进行中的水合任务。

**可能原因**

调用hydratePlaceholder取消水合（callbackType取CANCEL_FETCH_DATA）时，目标文件不存在进行中的水合任务。

**处理步骤**

无需处理。

## 34400034 活跃水合任务数量达到上限

**错误信息**

The number of active placeholder hydration tasks has reached the limit.

**错误描述**

活跃水合任务数量达到上限。

**可能原因**

单个云盘应用的活跃水合任务数达到5个，或全局活跃水合任务数达到10个。

**处理步骤**

等待部分水合任务完成或取消部分任务后再重试。
