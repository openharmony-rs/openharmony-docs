# renameSync

## renameSync

```TypeScript
declare function renameSync(oldPath: string, newPath: string): void
```

以同步方法重命名文件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [renameSync](arkts-corefile-file-fs-renamesync-f.md#renameSync)

<!--Device-unnamed-declare function renameSync(oldPath: string, newPath: string): void--><!--Device-unnamed-declare function renameSync(oldPath: string, newPath: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 目标文件的当前应用沙箱路径。 |
| newPath | string | 是 | 目标文件的新应用沙箱路径。 |

