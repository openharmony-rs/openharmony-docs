# closeSync

## closeSync

```TypeScript
declare function closeSync(fd: number): void
```

以同步方法关闭文件。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [@ohos.file.fs:closeSync](arkts-corefile-fileio-closesync-f.md#closesync)

<!--Device-unnamed-declare function closeSync(fd: number): void--><!--Device-unnamed-declare function closeSync(fd: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待关闭文件的文件描述符。 |

