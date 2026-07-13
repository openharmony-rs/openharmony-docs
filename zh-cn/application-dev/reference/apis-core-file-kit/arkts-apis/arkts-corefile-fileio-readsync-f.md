# readSync

## readSync

```TypeScript
declare function readSync(
  fd: number,
  buffer: ArrayBuffer,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
  }
): number
```

以同步方法从文件读取数据。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:readSync](arkts-corefile-file-fs-readsync-f.md#readsync-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待读取文件的文件描述符。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | {    offset?: number;    length?: number;    position?: number;  } | 否 | 支持如下选项：<br/>-?offset，number类型，表示将数据读取到缓冲区的位置，即相对于缓冲区首地址的偏移，单位为Byte。可选，默认为0。<br/>-?length，number类型，表示期望读取数据的长度。可选，默认缓冲区长度减去偏移长度，单位为Byte。<br/>-?position，number类型，表示期望读取文件的位置。可选，默认从当前位置开始读，单位为Byte。&lt;br/&gt;约束：offset+length&lt;=buffer.size。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 实际读取的长度，单位为Byte。 |

