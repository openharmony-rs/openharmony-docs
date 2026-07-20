# renameSync

<a id="renamesync"></a>
## renameSync

```TypeScript
declare function renameSync(oldPath: string, newPath: string): void
```

以同步方法重命名文件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:renameSync](arkts-corefile-file-fs-renamesync-f.md#renamesync-1)

<!--Device-unnamed-declare function renameSync(oldPath: string, newPath: string): void--><!--Device-unnamed-declare function renameSync(oldPath: string, newPath: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |

