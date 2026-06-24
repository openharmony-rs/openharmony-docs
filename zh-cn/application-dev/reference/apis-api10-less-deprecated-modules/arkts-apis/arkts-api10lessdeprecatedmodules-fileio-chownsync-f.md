# chownSync

## chownSync

```TypeScript
declare function chownSync(path: string, uid: number, gid: number): void
```

以同步的方法基于文件路径改变文件所有者。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待改变文件的应用沙箱路径。 |
| uid | number | 是 | 新的UID。 |
| gid | number | 是 | 新的GID。 |

