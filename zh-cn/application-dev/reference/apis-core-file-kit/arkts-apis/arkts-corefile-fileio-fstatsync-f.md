# fstatSync

## 导入模块

```TypeScript
```

## fstatSync

```TypeScript
declare function fstatSync(fd: number): Stat
```

以同步方法基于文件描述符获取文件状态信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [statSync](arkts-corefile-file-fs-statsync-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待获取文件状态的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stat](arkts-corefile-fileio-stat-depr-i.md) | 表示文件状态的具体信息。 |

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
let stat = fileio.fstatSync(fd);
```
