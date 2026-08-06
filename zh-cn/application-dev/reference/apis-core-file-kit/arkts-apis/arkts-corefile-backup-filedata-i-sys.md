# FileData（系统接口）

文件数据，包含一个已经打开的文件描述符，在与备份服务进行IPC时使用。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-backup-interface FileData--><!--Device-backup-interface FileData-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## fd

```TypeScript
fd: int
```

已经打开的文件描述符，通过备份服务获取，可用于读取或写入备份、恢复文件内容。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-FileData-fd: int--><!--Device-FileData-fd: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

