# read

## read

```TypeScript
declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
  }
): Promise<ReadOut>
```

从文件读取数据，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:read](arkts-corefile-file-fs-read-f.md#read-1)

<!--Device-unnamed-declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
  }
): Promise<ReadOut>--><!--Device-unnamed-declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options?: {
    offset?: number;
    length?: number;
    position?: number;
  }
): Promise<ReadOut>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待读取文件的文件描述符。 |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | {     offset?: number;     length?: number;     position?: number;   } | 否 | 支持如下选项：<br/>-?offset，number类型，表示将数据读取到缓冲区的位置，即相对于缓冲区首地址的偏移，单位为Byte。可选，默认为0。<br/>-?length，number类型，表示期望读取数据的长度。可选，默认缓冲区长度减去偏移长度，单位为Byte。<br/>-?position，number类型，表示期望读取文件的位置。可选，默认从当前位置开始读，单位为Byte。<br/>约束：offset+length&lt;=buffer.size。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ReadOut> | Promise对象。返回读取的结果。 |


## read

```TypeScript
declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback<ReadOut>): void
```

从文件读取数据，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:read](arkts-corefile-file-fs-read-f.md#read-1)

<!--Device-unnamed-declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback<ReadOut>): void--><!--Device-unnamed-declare function read(fd: number, buffer: ArrayBuffer, callback: AsyncCallback<ReadOut>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待读取文件的文件描述符。 |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 用于保存读取到的文件数据的缓冲区。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ReadOut> | 是 | 异步读取数据之后的回调。 |


## read

```TypeScript
declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options: {
    offset?: number;
    length?: number;
    position?: number;
  },
  callback: AsyncCallback<ReadOut>
): void
```

从文件读取数据，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:read](arkts-corefile-file-fs-read-f.md#read-1)

<!--Device-unnamed-declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options: {
    offset?: number;
    length?: number;
    position?: number;
  },
  callback: AsyncCallback<ReadOut>
): void--><!--Device-unnamed-declare function read(
  fd: number,
  buffer: ArrayBuffer,
  options: {
    offset?: number;
    length?: number;
    position?: number;
  },
  callback: AsyncCallback<ReadOut>
): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待读取文件的文件描述符。 |
| buffer | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | {     offset?: number;     length?: number;     position?: number;   } | 是 | 支持如下选项：<br/>-?offset，number类型，表示将数据读取到缓冲区的位置，单位为Byte，即相对于缓冲区首地址的偏移。可选，默认为0。<br/>-?length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度减去偏移长度。<br/>-?position，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>约束：offset+length&lt;=buffer.size。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<ReadOut> | 是 | 异步读取数据之后的回调。 |

