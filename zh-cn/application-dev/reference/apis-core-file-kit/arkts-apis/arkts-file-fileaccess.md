# @ohos.file.fileAccess

fileAccess模块是基于[extension](../../../../application-models/extensionability-overview.md)机制实现的一个对公共文件访问和操作的框架。该模块一方面对接各类文
件管理服务，如存储管理服务等；另一方面为系统应用提供一套统一的文件访问管理接口。存储管理服务可以管理内置存储部分目录，以及共享盘、U盘、SD卡等设备上的资源。

> **说明：**
>
> - 当前只支持FilePicker、文件管理器调用。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** [fs:fileIo](arkts-corefile-fileio-n.md)

**系统能力：** SystemCapability.FileManagement.UserFileService

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createFileAccessHelper](arkts-corefile-createfileaccesshelper-f-sys.md#createfileaccesshelper-1) | 以同步方法创建连接当前系统内所有文件管理服务的helper对象。 |
| [createFileAccessHelper](arkts-corefile-createfileaccesshelper-f-sys.md#createfileaccesshelper-2) | 以同步方法创建连接指定wants的helper对象。 |
| [getFileAccessAbilityInfo](arkts-corefile-getfileaccessabilityinfo-f-sys.md#getfileaccessabilityinfo-1) | 以异步方法获取系统内extension配置为fileAccess类型的所有Want信息。使用callback异步回调。 |
| [getFileAccessAbilityInfo](arkts-corefile-getfileaccessabilityinfo-f-sys.md#getfileaccessabilityinfo-2) | 以异步方法获取系统内extension配置为fileAccess类型的所有Want信息。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CopyResult](arkts-corefile-copyresult-i-sys.md) | 表示复制操作失败时的返回信息，复制成功时则没有返回信息。 |
| [FileAccessHelper](arkts-corefile-fileaccesshelper-i-sys.md) | FileAccessHelper对象。 |
| [FileInfo](arkts-corefile-fileinfo-i-sys.md) | 表示文件(夹)属性信息和接口能力。 |
| [FileIterator](arkts-corefile-fileiterator-i-sys.md) | 表示文件夹的迭代器对象。 |
| [MoveResult](arkts-corefile-moveresult-i-sys.md) | 表示移动操作失败时的返回信息，移动成功时则没有返回信息。 |
| [NotifyMessage](arkts-corefile-notifymessage-i-sys.md) | 通知回调函数的值。 |
| [RootInfo](arkts-corefile-rootinfo-i-sys.md) | 表示设备的根属性信息和接口能力。 |
| [RootIterator](arkts-corefile-rootiterator-i-sys.md) | 表示设备根目录的迭代器对象。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FileKey](arkts-corefile-filekey-e-sys.md) | Property elements that support the file queries. |
| [NotifyType](arkts-corefile-notifytype-e-sys.md) | 枚举，通知类型。 |
| [OPENFLAGS](arkts-corefile-openflags-e-sys.md) | 枚举，目前支持的文件打开的标志位。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DEVICES_URI](arkts-corefile-fileaccess-con-sys.md#devices_uri) | 监听设备上线，下线通知，作为注册监听的URI。 |
<!--DelEnd-->

