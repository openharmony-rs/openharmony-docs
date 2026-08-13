# opendirSync

## opendirSync

```TypeScript
declare function opendirSync(path: string): Dir
```

以同步方法打开文件目录。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [listFileSync](arkts-corefile-file-fs-listfilesync-f.md#listFileSync)

<!--Device-unnamed-declare function opendirSync(path: string): Dir--><!--Device-unnamed-declare function opendirSync(path: string): Dir-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待打开文件目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Dir](arkts-corefile-fileio-dir-depr-i.md) | 返回Dir对象。 |

