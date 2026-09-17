# @ohos.file.backup

Module providing backup and restore capabilities.

@namespace backup

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [fileSystemServiceRequest](arkts-corefile-backup-filesystemservicerequest-f-sys.md) | Requests filesystem garbage collection with specified configuration. |
| [getBackupInfo](arkts-corefile-backup-getbackupinfo-f-sys.md) | Get Backup information from bundle. |
| [getBackupVersion](arkts-corefile-backup-getbackupversion-f-sys.md) | Obtain the backupVersion. |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md) | Obtain a Json file that describes local capabilities. |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md) | Obtain a Json file that describes local capabilities. |
| [getLocalCapabilities](arkts-corefile-backup-getlocalcapabilities-f-sys.md) | Obtain a json file that describes local capabilities. |
| [updateSendRate](arkts-corefile-backup-updatesendrate-f-sys.md) | Update send file fd rate. |
| [updateTimer](arkts-corefile-backup-updatetimer-f-sys.md) | Update backup or restore timeout. |
<!--DelEnd-->

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [IncrementalBackupSession](arkts-corefile-backup-incrementalbackupsession-c-sys.md) | Control class for incremental backup procedure. |
| [SessionBackup](arkts-corefile-backup-sessionbackup-c-sys.md) | Control class for backup procedure. |
| [SessionRestore](arkts-corefile-backup-sessionrestore-c-sys.md) | Control class for restore procedure. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BackupParams](arkts-corefile-backup-backupparams-i-sys.md) | Provides configuration parameters for backup and restore. |
| [BackupPriority](arkts-corefile-backup-backuppriority-i-sys.md) | Control backup and restore priority sequence |
| [File](arkts-corefile-backup-file-i-sys.md) | Corresponds to a file, including its metadata and data and the file's manifest data. Files are useful as IPC and backup services. |
| [FileData](arkts-corefile-backup-filedata-i-sys.md) | Corresponding to a file's data. Filedata is useful when doing IPC with the backup service. |
| [FileManifestData](arkts-corefile-backup-filemanifestdata-i-sys.md) | Manifest file information in incremental data. FileManifestData is useful when doing IPC with the backup service. |
| [FileMeta](arkts-corefile-backup-filemeta-i-sys.md) | Corresponding to a file's metadata. FileMeta is useful when doing IPC with the backup service. |
| [FileSystemRequestConfig](arkts-corefile-backup-filesystemrequestconfig-i-sys.md) | Parameters required to perform garbage collection (GC). |
| [GeneralCallbacks](arkts-corefile-backup-generalcallbacks-i-sys.md) | General callbacks for both backup and restore procedure. The backup service will notify the client by these callbacks. |
| [IncrementalBackupData](arkts-corefile-backup-incrementalbackupdata-i-sys.md) | Corresponds to an incremental application, including its last incremental time and incremental list. |
| [IncrementalBackupTime](arkts-corefile-backup-incrementalbackuptime-i-sys.md) | Save the time information of the incremental backup. IncrementalBackupTime is useful when doing IPC with the backup service. |
| [PathInfo](arkts-corefile-backup-pathinfo-i-sys.md) | Path information for file migration. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [OnBackupSizeReport](arkts-corefile-backup-onbackupsizereport-t-sys.md) | function that returns backup datasize by bundleName. |
| [OnFileReadyBatch](arkts-corefile-backup-onfilereadybatch-t-sys.md) | Function that returns array of file handle. |
<!--DelEnd-->
