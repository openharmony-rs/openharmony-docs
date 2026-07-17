# mkdirSync

## mkdirSync

```TypeScript
declare function mkdirSync(path: string, mode?: number): void
```

以同步方法创建目录。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirsync-1)

<!--Device-unnamed-declare function mkdirSync(path: string, mode?: number): void--><!--Device-unnamed-declare function mkdirSync(path: string, mode?: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待创建目录的应用沙箱路径。 |
| mode | number | 否 | 创建目录的权限，可给定如下权限，以按位或的方式追加权限，默认给定0o775。<br/>-?0o775：所有者具有读、写及可执行权限，其余用户具有读及可执行权限。<br/>-?0o700：所有者具有读、写及可执行权限。<br/>-?0o400：所有者具有读权限。<br/>-?0o200：所有者具有写权限。<br/>-?0o100：所有者具有可执行权限。<br/>-?0o070：所有用户组具有读、写及可执行权限。<br/>-?0o040：所有用户组具有读权限。<br/>-?0o020：所有用户组具有写权限。<br/>-?0o010：所有用户组具有可执行权限。<br/>-?0o007：其余用户具有读、写及可执行权限。<br/>-?0o004：其余用户具有读权限。<br/>-?0o002：其余用户具有写权限。<br/>-?0o001：其余用户具有可执行权限。 |

