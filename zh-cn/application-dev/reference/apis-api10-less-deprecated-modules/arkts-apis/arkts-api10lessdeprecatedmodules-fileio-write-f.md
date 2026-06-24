# write

## write

```TypeScript
declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
    encoding?: string;
  }
): Promise<number>
```

将数据写入文件，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:write](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-write-f.md#write-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待写入文件的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | {<br/>    offset?: number;<br/>    length?: number;<br/>    position?: number;<br/>    encoding?: string;<br/>  } | 否 | 支持如下选项：<br/>-?offset，number类型，表示期望写入数据的位置相对于数据首地址的偏移，单位为Byte。可选，默认为0。<br/>-?length，<br/>number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?position，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>-?<br/>encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认?'utf-8'。仅支持?'utf-8'。<br/>约束：offset+length } Promise对象。返回实际写入的长度，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; |  |


## write

```TypeScript
declare function write(fd: number, buffer: ArrayBuffer | string, callback: AsyncCallback<number>): void
```

将数据写入文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:write](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-write-f.md#write-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待写入文件的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 异步将数据写入完成后执行的回调函数。返回实际写入的长度，单位为Byte。 |


## write

```TypeScript
declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options: {
    offset?: number;
    length?: number;
    position?: number;
    encoding?: string;
  },
  callback: AsyncCallback<number>
): void
```

将数据写入文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:write](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-write-f.md#write-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待写入文件的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | {<br/>    offset?: number;<br/>    length?: number;<br/>    position?: number;<br/>    encoding?: string;<br/>  } | 是 | 支持如下选项：<br/>-?offset，number类型，表示期望写入数据的位置相对于数据首地址的偏移，单位为Byte。可选，默认为0。<br/>-?length，<br/>number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?position，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>-?<br/>encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认?'utf-8'。仅支持?'utf-8'。<br/>约束：offset+length } [callback] - 异步将数据写入完成后执行的回调函数。返回实际写入的长度，单位为Byte。 |
| callback | AsyncCallback&lt;number&gt; | 是 |  |

