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

The input parameter is invalid.

**错误描述**

输入参数无效。

**可能原因**

文件路径为空、不是绝对路径、包含非法路径段（如“..”或“.”），或枚举参数取值不在允许范围内。

**处理步骤**

检查并修正入参后重试。

## 34400003 IPC通信失败

**错误信息**

IPC communication failed.

**错误描述**

IPC通信失败。

**可能原因**

调用服务不存在。

**处理步骤**

检查服务是否启动。

## 34400008 同步根路径未注册

**错误信息**

No sync root is registered, or the registered sync roots cannot be queried.

**错误描述**

同步根路径未注册，或已注册的同步根信息查询失败。

**可能原因**

目标路径不在任何已注册的同步根目录范围内，或系统查询已注册同步根信息失败。

**处理步骤**

可调用[getAllSyncFolders](js-apis-file-clouddiskmanager-sys.md#getallsyncfolders)()查询已注册的同步根列表，确认目标路径位于同步根目录范围内后重试。

## 34400010 同步根路径不存在

**错误信息**

The sync root path does not exist, or the target file or sync root mount path is missing during path resolution.

**错误描述**

同步根路径不存在，或路径解析时目标文件、挂载路径缺失。

**可能原因**

同步根目录已被删除或未挂载，或目标文件在路径解析时不存在。

**处理步骤**

确认同步根路径存在且目标文件路径有效后重试。

## 34400014 系统内部错误

**错误信息**

Temporary failure. Retry is recommended (e.g., network issues).

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

可调用[getAllSyncFolders](js-apis-file-clouddiskmanager-sys.md#getallsyncfolders)()确认目标文件位于三方网盘应用已注册的同步根目录内，且为网盘应用创建的文件（本地仅保留元数据、内容在云侧）后再调用。

## 34400019 水合任务已在进行中

**错误信息**

A hydrate task for the target file is already pending or in progress.

**错误描述**

目标文件已存在进行中的水合任务。

**可能原因**

同一文件的水合任务尚未完成或未取消时再次发起水合，或水合进行中调用脱水接口。

**处理步骤**

等待水合完成，或先调用[hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)()（callbackType取CANCEL_FETCH_DATA）取消水合任务后再操作。

## 34400020 磁盘可用空间不足

**错误信息**

The available disk space is insufficient, or the disk quota has been exhausted.

**错误描述**

磁盘可用空间不足，或磁盘配额已用尽。

**可能原因**

执行脱水时本地磁盘可用空间不足，或应用的磁盘配额已用尽。

**处理步骤**

清理本地存储空间或提升磁盘配额后重试。

## 34400021 回调表未注册

**错误信息**

The cloud disk provider's callback table is not registered, or no usable sync root matches the path.

**错误描述**

网盘应用回调表未注册，或没有匹配该路径的可用同步根。

**可能原因**

目标路径不在任何已注册的同步根目录范围内，或目标路径所属同步根对应的三方网盘应用未注册回调表。

**处理步骤**

确认目标路径位于已注册的同步根目录范围内，且对应的三方网盘应用已完成回调表注册。

## 34400023 路径父目录不是目录

**错误信息**

A path component that must be a directory is not a directory.

**错误描述**

目标路径中本应为目录的路径段不是目录。

**可能原因**

目标路径的某个路径段实际为普通文件，导致路径解析失败。

**处理步骤**

请检查目标路径中的各级路径段是否均为目录（可通过[@ohos.file.fs](js-apis-file-fs.md)的[statSync](js-apis-file-fs.md#fileiostatsync)接口判断路径段是否为目录），修正目标路径后重试。

## 34400024 目标路径不存在

**错误信息**

A required file or directory does not exist while resolving or accessing the target path.

**错误描述**

访问解析后的路径时目标路径不存在。

**可能原因**

目标文件或其路径中的某个路径段已被删除或移动。

**处理步骤**

确认目标文件存在后重试。

## 34400025 文件名或路径过长

**错误信息**

The file name or path is too long.

**错误描述**

文件名或路径超出系统允许的最大长度。

**可能原因**

传入的文件路径或其中的文件名超出系统限制。

**处理步骤**

单个文件名最长255字节、完整路径最长4096字节，请缩短文件名或路径后重试。

## 34400029 网盘应用拒绝脱水

**错误信息**

The cloud disk provider did not approve the dehydration request.

**错误描述**

三方网盘应用拒绝了脱水授权。

**可能原因**

脱水前系统向三方网盘应用发起脱水授权请求，网盘应用返回不允许脱水（如文件正在被云侧使用）。

**处理步骤**

该错误表示三方网盘应用未授权本次脱水，文件保持不变，无需处理。

## 34400031 占位符文件已完全水合

**错误信息**

The placeholder is already fully hydrated.

**错误描述**

占位符文件已完全水合，无需再次水合。

**可能原因**

对已完全水合的占位符文件再次发起水合。

**处理步骤**

无需处理。水合在原路径完成，文件内容写入调用[hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)()时传入的filePath路径，可直接访问。

## 34400032 无进行中的水合任务

**错误信息**

Cancellation was requested, but no hydrate task is pending or in progress.

**错误描述**

目标文件不存在进行中的水合任务。

**可能原因**

调用[hydratePlaceholder](js-apis-file-clouddiskmanager-sys.md#hydrateplaceholder)()取消水合（callbackType取CANCEL_FETCH_DATA）时，目标文件不存在进行中的水合任务。

**处理步骤**

无需处理。

## 34400033 占位符状态无效

**错误信息**

The placeholder state or its stored attribute is invalid.

**错误描述**

占位符文件存储的状态或属性无效。

**可能原因**

占位符文件的状态值不在有效范围内，或其记录的属性信息损坏。

**处理步骤**

请确认占位符文件由三方网盘应用正常创建、状态值在有效范围内后重试；若持续出现该错误，请三方网盘应用重建该占位符文件。

## 34400034 活跃水合任务数量达到上限

**错误信息**

The limit on pending hydrate tasks has been reached.

**错误描述**

待处理（排队中）的水合任务数量达到上限。

**可能原因**

单个网盘应用或全局处于待处理状态的水合任务数达到系统上限。

**处理步骤**

请等待部分水合任务完成或取消后再重试；可通过[onHydrateProgress](js-apis-file-clouddiskmanager-sys.md#onhydrateprogress)()订阅水合进度事件，在收到COMPLETED或CANCELLED状态后再发起水合。
