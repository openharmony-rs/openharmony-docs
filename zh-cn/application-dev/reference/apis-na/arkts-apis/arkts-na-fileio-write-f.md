# write

## 导入模块

```TypeScript
```

## write

```TypeScript
function write(
  fd: int,
  buffer: ArrayBuffer | string,
  options?: WriteOptions
): Promise<long>
```

将数据写入文件，返回实际写入的字节数。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function write(  fd: int,  buffer: ArrayBuffer | string,  options?: WriteOptions): Promise<long>--><!--Device-fileIo-function write(  fd: int,  buffer: ArrayBuffer | string,  options?: WriteOptions): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](arkts-na-file-fs-writeoptions-i.md) | 否 | 支持如下选项：<br/>- offset，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写入。<br/>-  length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。 当前仅支持 'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回实际写入的数据长度，单位为Byte。 |

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
function write(fd: int, buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void
```

将数据写入文件，返回实际写入的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function write(fd: int, buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void--><!--Device-fileIo-function write(fd: int, buffer: ArrayBuffer | string, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际写入的数据长度，单位为Byte。 |

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
function write(
  fd: int,
  buffer: ArrayBuffer | string,
  options: WriteOptions,
  callback: AsyncCallback<long>
): void
```

将数据写入文件，支持配置写入选项（如偏移位置和写入长度），返回实际写入的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function write(  fd: int,  buffer: ArrayBuffer | string,  options: WriteOptions,  callback: AsyncCallback<long>): void--><!--Device-fileIo-function write(  fd: int,  buffer: ArrayBuffer | string,  options: WriteOptions,  callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](arkts-na-file-fs-writeoptions-i.md) | 是 | 支持如下选项：<br/>- offset，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>- length， number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。 当前仅支持 'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际写入的数据长度，单位为Byte。 |

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

