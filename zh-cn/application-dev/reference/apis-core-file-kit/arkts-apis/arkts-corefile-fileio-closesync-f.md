# closeSync

## 导入模块

```TypeScript
```

## closeSync

```TypeScript
declare function closeSync(fd: number): void
```

以同步方法关闭文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [closeSync](arkts-corefile-file-fs-closesync-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待关闭文件的文件描述符。 |

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
fileio.closeSync(fd);
```
