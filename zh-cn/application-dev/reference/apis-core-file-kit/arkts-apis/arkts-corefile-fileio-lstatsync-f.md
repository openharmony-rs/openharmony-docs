# lstatSync

## lstatSync

```TypeScript
declare function lstatSync(path: string): Stat
```

以同步方法获取链接信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:lstatSync](arkts-corefile-file-fs-lstatsync-f.md#lstatsync-1)

<!--Device-unnamed-declare function lstatSync(path: string): Stat--><!--Device-unnamed-declare function lstatSync(path: string): Stat-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目标文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stat](arkts-corefile-file-fs-stat-i.md) | 表示文件的具体信息。 |

