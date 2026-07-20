# fchownSync

<a id="fchownsync"></a>
## fchownSync

```TypeScript
declare function fchownSync(fd: number, uid: number, gid: number): void
```

以同步方法基于文件描述符改变文件所有者。

**起始版本：** 7

**废弃版本：** 9

<!--Device-unnamed-declare function fchownSync(fd: number, uid: number, gid: number): void--><!--Device-unnamed-declare function fchownSync(fd: number, uid: number, gid: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| uid | number | 是 | 文件所有者的UID。 |
| gid | number | 是 | 文件所有组的GID。 |

