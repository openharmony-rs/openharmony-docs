# HistoryVersion

端云文件历史版本信息，调用端云文件版本管理类[FileVersion](arkts-corefile-cloudsync-fileversion-c.md#FileVersion)的 [gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#getHistoryVersionList)方法时，历史版本列表中的属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cloudSync-interface HistoryVersion--><!--Device-cloudSync-interface HistoryVersion-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## autoResolved

```TypeScript
autoResolved: boolean
```

当前版本是否为自动解决冲突的版本。 应用设置手动解冲突时，默认返回false，无意义。 应用设置自动解冲突时，端侧会自动解冲突，true表示当前版本存在冲突，端云服务已自动解决冲突，false表示无冲突，未自动解冲突。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-autoResolved: boolean--><!--Device-HistoryVersion-autoResolved: boolean-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## editedTime

```TypeScript
editedTime: long
```

文件内容修改的时间戳，单位：ms。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-editedTime: long--><!--Device-HistoryVersion-editedTime: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## fileSize

```TypeScript
fileSize: long
```

文件大小，单位：Byte。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-fileSize: long--><!--Device-HistoryVersion-fileSize: long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## originalFileName

```TypeScript
originalFileName: string
```

当前版本对应的文件名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-originalFileName: string--><!--Device-HistoryVersion-originalFileName: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## sha256

```TypeScript
sha256: string
```

当前版本对应文件内容的哈希值。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-sha256: string--><!--Device-HistoryVersion-sha256: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## versionId

```TypeScript
versionId: string
```

文件版本号。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HistoryVersion-versionId: string--><!--Device-HistoryVersion-versionId: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

