# accessSync

## accessSync

```TypeScript
declare function accessSync(path: string, mode?: number): void
```

以同步方法检查当前进程是否可访问某文件。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [accessSync](arkts-corefile-file-fs-accesssync-f.md#accessSync)

<!--Device-unnamed-declare function accessSync(path: string, mode?: number): void--><!--Device-unnamed-declare function accessSync(path: string, mode?: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待访问文件的应用沙箱路径。 |
| mode | number | 否 | 访问文件时的选项，可给定如下选项，以按位或的方式使用多个选项，默认给定0。&lt;br/&gt;确认当前进程是否具有对应权限：&lt;br/&gt;-?0：确认文件是否存在。&lt;br/&gt;-?1：确认当前进程 是否具有可执行权限。&lt;br/&gt;-?2：确认当前进程是否具有写权限。&lt;br/&gt;-?4：确认当前进程是否具有读权限。 |

