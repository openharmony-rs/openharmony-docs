# statSync

## statSync

```TypeScript
declare function statSync(path: string): Stat
```

以同步方法获取文件的信息。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:statSync](arkts-corefile-file-fs-statsync-f.md#statsync-1)

<!--Device-unnamed-declare function statSync(path: string): Stat--><!--Device-unnamed-declare function statSync(path: string): Stat-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待获取文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stat](arkts-corefile-file-fs-stat-i.md) | 表示文件的具体信息。 |

