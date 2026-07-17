# truncateSync

## truncateSync

```TypeScript
declare function truncateSync(path: string, len?: number): void
```

以同步方法基于文件路径截断文件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:truncateSync](arkts-corefile-file-fs-truncatesync-f.md#truncatesync-1)

<!--Device-unnamed-declare function truncateSync(path: string, len?: number): void--><!--Device-unnamed-declare function truncateSync(path: string, len?: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待截断文件的应用沙箱路径。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

