# RandomAccessFile

随机读写文件流，提供基于偏移指针的随机读写能力。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-interface RandomAccessFile--><!--Device-fileIo-interface RandomAccessFile-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## close

```TypeScript
close(): void
```

以同步方式关闭RandomAccessFile对象，关闭后不可再用于读写等操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-close(): void--><!--Device-RandomAccessFile-close(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

## getReadStream

```TypeScript
getReadStream(): ReadStream
```

获取当前RandomAccessFile的一个ReadStream实例，用于流式读取文件数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-getReadStream(): ReadStream--><!--Device-RandomAccessFile-getReadStream(): ReadStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReadStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readstream-c.md) | 文件可读流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error |
| 13900012 | Permission denied |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

## getWriteStream

```TypeScript
getWriteStream(): WriteStream
```

获取当前RandomAccessFile的一个WriteStream实例，用于流式写入文件数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-getWriteStream(): WriteStream--><!--Device-RandomAccessFile-getWriteStream(): WriteStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WriteStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writestream-c.md) | 文件可写流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error |
| 13900012 | Permission denied |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

## read

```TypeScript
read(
    buffer: ArrayBuffer,
    options?: ReadOptions
  ): Promise<long>
```

从文件读取数据，返回实际读取的字节数。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-read(    buffer: ArrayBuffer,    options?: ReadOptions  ): Promise<long>--><!--Device-RandomAccessFile-read(    buffer: ArrayBuffer,    options?: ReadOptions  ): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于读取文件的缓冲区。 |
| options | [ReadOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认为缓冲区长度。&lt;br/&gt;- offset， number类型，表示期望读取文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始读。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回读取的结果，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900034 | Operation would block |
| 13900019 | Is a directory |
| 13900044 | Network is unreachable |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |

## read

```TypeScript
read(buffer: ArrayBuffer, callback: AsyncCallback<long>): void
```

从文件读取数据，返回实际读取的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-read(buffer: ArrayBuffer, callback: AsyncCallback<long>): void--><!--Device-RandomAccessFile-read(buffer: ArrayBuffer, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于读取文件的缓冲区。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900034 | Operation would block |
| 13900019 | Is a directory |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |

## read

```TypeScript
read(
    buffer: ArrayBuffer,
    options: ReadOptions,
    callback: AsyncCallback<long>
  ): void
```

从文件读取数据，支持配置读取选项，返回实际读取的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-read(    buffer: ArrayBuffer,    options: ReadOptions,    callback: AsyncCallback<long>  ): void--><!--Device-RandomAccessFile-read(    buffer: ArrayBuffer,    options: ReadOptions,    callback: AsyncCallback<long>  ): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于读取文件的缓冲区。 |
| options | [ReadOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readoptions-i.md) | 是 | 支持如下选项：&lt;br/&gt;- length，number类型，表示读取数据的长度，单位为Byte。可选，默认为缓冲区长度。&lt;br/&gt;- offset， number类型，表示读取文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从filePointer开始读。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900034 | Operation would block |
| 13900019 | Is a directory |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |

## readSync

```TypeScript
readSync(
    buffer: ArrayBuffer,
    options?: ReadOptions
  ): long
```

以同步方法从文件读取数据，返回实际读取的字节数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-readSync(    buffer: ArrayBuffer,    options?: ReadOptions  ): long--><!--Device-RandomAccessFile-readSync(    buffer: ArrayBuffer,    options?: ReadOptions  ): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于读取文件的缓冲区。 |
| options | [ReadOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- length，number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。&lt;br/&gt;- offset， number类型，表示期望读取文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始读。&lt;br/&gt; |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 实际读取的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900034 | Operation would block |
| 13900019 | Is a directory |
| 13900044 | Network is unreachable |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |

## setFilePointer

```TypeScript
setFilePointer(filePointer: long): void
```

设置文件偏移指针，用于指定后续读写等操作的起始位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-setFilePointer(filePointer: long): void--><!--Device-RandomAccessFile-setFilePointer(filePointer: long): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePointer | long | 是 | RandomAccessFile对象的偏移指针，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |

## write

```TypeScript
write(
    buffer: ArrayBuffer | string,
    options?: WriteOptions
  ): Promise<long>
```

将数据写入文件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-write(    buffer: ArrayBuffer | string,    options?: WriteOptions  ): Promise<long>--><!--Device-RandomAccessFile-write(    buffer: ArrayBuffer | string,    options?: WriteOptions  ): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writeoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- length，number类型，表示期望写入数据的长度，单位为Byte。默认缓冲区长度。&lt;br/&gt;- offset， number类型，表示期望写入文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始写。&lt;br/&gt;- encoding， string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。仅支持 'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

## write

```TypeScript
write(buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void
```

将数据写入文件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-write(buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void--><!--Device-RandomAccessFile-write(buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际写入数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

## write

```TypeScript
write(
    buffer: ArrayBuffer | string,
    options: WriteOptions,
    callback: AsyncCallback<long>
  ): void
```

将数据写入文件，支持配置写入选项。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-write(    buffer: ArrayBuffer | string,    options: WriteOptions,    callback: AsyncCallback<long>  ): void--><!--Device-RandomAccessFile-write(    buffer: ArrayBuffer | string,    options: WriteOptions,    callback: AsyncCallback<long>  ): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writeoptions-i.md) | 是 | 支持如下选项：&lt;br/&gt;- length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认为缓冲区长度。&lt;br/&gt;- offset， number类型，表示期望写入文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始写。&lt;br/&gt;- encoding， string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。仅支持 'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际写入数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

## writeSync

```TypeScript
writeSync(
    buffer: ArrayBuffer | string,
    options?: WriteOptions
  ): long
```

以同步方法将数据写入文件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-writeSync(    buffer: ArrayBuffer | string,    options?: WriteOptions  ): long--><!--Device-RandomAccessFile-writeSync(    buffer: ArrayBuffer | string,    options?: WriteOptions  ): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writeoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。&lt;br/&gt;- offset， number类型，表示期望写入文件位置，单位为Byte（基于当前filePointer加上offset的位置）。可选，默认从偏移指针（filePointer）开始写。&lt;br/&gt;- encoding， string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。仅支持 'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

## fd

```TypeScript
readonly fd: int
```

已打开的文件描述符fd。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-readonly fd: int--><!--Device-RandomAccessFile-readonly fd: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## filePointer

```TypeScript
readonly filePointer: long
```

RandomAccessFile对象的偏移指针，表示当前读写位置，单位为Byte。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-RandomAccessFile-readonly filePointer: long--><!--Device-RandomAccessFile-readonly filePointer: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

