# OnBackupSizeReport（系统接口）

```TypeScript
type OnBackupSizeReport = (reportInfo: string) => void
```

返回应用备份数据量信息的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backup-type OnBackupSizeReport = (reportInfo: string) => void--><!--Device-backup-type OnBackupSizeReport = (reportInfo: string) => void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reportInfo | string | 是 | 框架扫描到的应用待备份数据量信息，为JSON格式字符串。 |

