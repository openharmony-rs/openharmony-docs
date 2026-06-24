# utimes

## utimes

```TypeScript
declare function utimes(path: string, mtime: number): void
```

更改文件上次修改该文件的时间。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径。 |
| mtime | number | 是 | 待更新的时间戳。自1970年1月1日起至目标时间的毫秒数。仅支持更改上次修改该文件的时间属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

