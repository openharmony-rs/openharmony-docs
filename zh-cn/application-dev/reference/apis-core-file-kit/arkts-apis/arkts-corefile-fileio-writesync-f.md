# writeSync

## writeSync

```TypeScript
declare function writeSync(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
    encoding?: string;
  }
): number
```

以同步方法将数据写入文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:writeSync](arkts-corefile-file-fs-writesync-f.md#writesync-1)

<!--Device-unnamed-declare function writeSync(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
    encoding?: string;
  }
): number--><!--Device-unnamed-declare function writeSync(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
    encoding?: string;
  }
): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待写入文件的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | {     offset?: number;     length?: number;     position?: number;     encoding?: string;   } | 否 | 支持如下选项：<br/>-?offset，number类型，表示期望写入数据的位置相对于数据首地址的偏移，单位为Byte。可选，默认为0。<br/>-?length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?position，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>-?encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认?'utf-8'。仅支持?'utf-8'。<br/>约束：offset+length&lt;=buffer.size。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 实际写入的长度，单位为Byte。 |

