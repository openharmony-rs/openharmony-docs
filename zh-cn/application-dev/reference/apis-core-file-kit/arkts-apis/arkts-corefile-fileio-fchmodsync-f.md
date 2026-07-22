# fchmodSync

## fchmodSync

```TypeScript
declare function fchmodSync(fd: number, mode: number): void
```

以同步方法基于文件描述符改变文件权限。

**起始版本：** 7

**废弃版本：** 9

<!--Device-unnamed-declare function fchmodSync(fd: number, mode: number): void--><!--Device-unnamed-declare function fchmodSync(fd: number, mode: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| mode | number | 是 | 若创建文件，则指定文件的权限，可给定如下权限，以按位或的方式追加权限。<br/>-?0o700：所有者具有读、写及可执行权限。<br/>-?0o400：所有者具有读权限。<br/>-?0o200：所有者具有写权限。<br/>-?0o100：所有者具有可执行权限。<br/>-?0o070：所有用户组具有读、写及可执行权限。<br/>-?0o040：所有用户组具有读权限。<br/>-?0o020：所有用户组具有写权限。<br/>-?0o010：所有用户组具有可执行权限。<br/>-?0o007：其余用户具有读、写及可执行权限。<br/>-?0o004：其余用户具有读权限。<br/>-?0o002：其余用户具有写权限。<br/>-?0o001：其余用户具有可执行权限。 |

