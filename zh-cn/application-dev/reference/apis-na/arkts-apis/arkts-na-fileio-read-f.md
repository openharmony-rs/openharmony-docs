# read

## 导入模块

```TypeScript
```

## read

```TypeScript
function read(
  fd: int,
  buffer: ArrayBuffer,
  options?: ReadOptions
): Promise<long>
```

从文件读取数据，返回实际读取的字节数。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function read(  fd: int,  buffer: ArrayBuffer,  options?: ReadOptions): Promise<long>--><!--Device-fileIo-function read(  fd: int,  buffer: ArrayBuffer,  options?: ReadOptions): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | [ReadOptions](arkts-na-file-fs-readoptions-i.md) | 否 | 支持如下选项：<br/>- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>- length， number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回实际读取的数据长度，单位为Byte。 |

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
function read(fd: int, buffer: ArrayBuffer, callback: AsyncCallback<long>): void
```

从文件读取数据，返回实际读取的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function read(fd: int, buffer: ArrayBuffer, callback: AsyncCallback<long>): void--><!--Device-fileIo-function read(fd: int, buffer: ArrayBuffer, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。返回实际读取的数据长度，单位为Byte。 |

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
function read(
  fd: int,
  buffer: ArrayBuffer,
  options: ReadOptions,
  callback: AsyncCallback<long>
): void
```

从文件读取数据，支持配置读取选项（如偏移位置和读取长度），返回实际读取的字节数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function read(  fd: int,  buffer: ArrayBuffer,  options: ReadOptions,  callback: AsyncCallback<long>): void--><!--Device-fileIo-function read(  fd: int,  buffer: ArrayBuffer,  options: ReadOptions,  callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | [ReadOptions](arkts-na-file-fs-readoptions-i.md) | 是 | 支持如下选项：<br/>- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>- length， number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数，返回实际读取的数据长度，单位为Byte。 |

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

