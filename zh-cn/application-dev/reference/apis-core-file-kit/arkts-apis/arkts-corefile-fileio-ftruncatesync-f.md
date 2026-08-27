# ftruncateSync

## 导入模块

```TypeScript
```

## ftruncateSync

```TypeScript
declare function ftruncateSync(fd: number, len?: number): void
```

以同步方法基于文件描述符截断文件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [truncateSync](arkts-corefile-file-fs-truncatesync-f.md)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待截断文件的文件描述符。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
let fd = fileio.openSync(filePath);
let len = 5;
fileio.ftruncateSync(fd, len);
```
