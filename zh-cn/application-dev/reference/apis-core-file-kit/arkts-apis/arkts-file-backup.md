# @ohos.file.backup

提供备份和恢复能力的模块。

**起始版本：** 10

<!--Device-unnamed-declare namespace backup--><!--Device-unnamed-declare namespace backup-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [fileSystemServiceRequest](arkts-corefile-backup-filesystemservicerequest-f-sys.md#filesystemservicerequest) | 根据指定配置请求文件系统执行碎片清理。 |
| [getBackupInfo](arkts-corefile-backup-getbackupinfo-f-sys.md#getbackupinfo) | 获取需要备份的应用信息。 |
| [getBackupVersion](arkts-corefile-backup-getbackupversion-f-sys.md#getbackupversion) | 获取备份版本信息。 |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md#getlocalcapabilities) | 获取描述本地能力的JSON文件。 |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md#getlocalcapabilities-1) | 获取描述本地能力的JSON文件。 |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md#getlocalcapabilities-2) | 获取描述本地能力的JSON文件。 |
| [updateSendRate](arkts-corefile-backup-updatesendrate-f-sys.md#updatesendrate) | 更新备份应用发送文件描述符的速率。 |
| [updateTimer](arkts-corefile-backup-updatetimer-f-sys.md#updatetimer) | 设置应用备份或恢复的时长。 |
<!--DelEnd-->

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IncrementalBackupSession](arkts-corefile-backup-incrementalbackupsession-c-sys.md) | 增量备份流程对象，用于支撑应用增量备份流程。 |
| [SessionBackup](arkts-corefile-backup-sessionbackup-c-sys.md) | 备份流程对象，用于支撑应用全量备份流程。 |
| [SessionRestore](arkts-corefile-backup-sessionrestore-c-sys.md) | 恢复流程对象，用于支撑应用全量恢复流程。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [File](arkts-corefile-backup-file-i.md) | 文件对象，包含文件元数据、文件数据和清单文件信息。用于客户端与备份服务进行IPC。 |
| [IncrementalBackupData](arkts-corefile-backup-incrementalbackupdata-i.md) | 一次增量备份对象，包含最后一次增量备份时间和增量清单。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BackupParams](arkts-corefile-backup-backupparams-i-sys.md) | 为备份恢复提供可选配置参数。 |
| [BackupPriority](arkts-corefile-backup-backuppriority-i-sys.md) | 控制备份和恢复的优先级顺序。 |
| [FileData](arkts-corefile-backup-filedata-i-sys.md) | 文件数据，包含一个已经打开的文件描述符，在与备份服务进行IPC时使用。 |
| [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md) | 增量数据中的清单文件信息，用于描述应用增量备份、恢复时对应文件的基础信息。 |
| [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | 文件的元数据，包含应用名称及文件URI，在与备份服务进行IPC时使用。 |
| [FileSystemRequestConfig](arkts-corefile-backup-filesystemrequestconfig-i-sys.md) | 配置系统执行碎片清理所需的参数。 |
| [GeneralCallbacks](arkts-corefile-backup-generalcallbacks-i-sys.md) | 备份和恢复过程中的通用回调。备份服务通过这些回调向客户端通知备份或恢复阶段。 |
| [IncrementalBackupTime](arkts-corefile-backup-incrementalbackuptime-i-sys.md) | 记录最后一次增量备份时间，用于描述备份增量的时间点。 |
| [PathInfo](arkts-corefile-backup-pathinfo-i-sys.md) | 文件迁移的路径信息。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [OnBackupSizeReport](arkts-corefile-backup-onbackupsizereport-t-sys.md) | 返回应用备份数据量信息的回调函数。 |
| [OnFileReadyBatch](arkts-corefile-backup-onfilereadybatch-t-sys.md) | 一批文件准备好发送给客户端时触发的回调函数。 |
<!--DelEnd-->

