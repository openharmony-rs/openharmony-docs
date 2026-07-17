# symlinkSync

## symlinkSync

```TypeScript
declare function symlinkSync(target: string, srcPath: string): void
```

以同步的方法基于文件路径创建符号链接。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:symlinkSync](arkts-corefile-file-fs-symlinksync-f.md#symlinksync-1)

<!--Device-unnamed-declare function symlinkSync(target: string, srcPath: string): void--><!--Device-unnamed-declare function symlinkSync(target: string, srcPath: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |

