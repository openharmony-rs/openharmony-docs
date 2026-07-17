# write

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## write

```TypeScript
declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: WriteOptions
): Promise<number>
```

将数据写入文件，使用promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: WriteOptions
): Promise<number>--><!--Device-unnamed-declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options?: WriteOptions
): Promise<number>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](arkts-corefile-file-fs-writeoptions-i.md) | 否 | 支持如下选项：<br/>- offset，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写入。<br/>- length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'。当前仅支持?'utf-8'。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回实际写入的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900013 | Bad address |
| 13900020 | Invalid argument |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900034 | Operation would block |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## write

```TypeScript
declare function write(fd: number, buffer: ArrayBuffer | string, callback: AsyncCallback<number>): void
```

将数据写入文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function write(fd: number, buffer: ArrayBuffer | string, callback: AsyncCallback<number>): void--><!--Device-unnamed-declare function write(fd: number, buffer: ArrayBuffer | string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 异步将数据写入完成后执行的回调函数。返回实际写入的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900013 | Bad address |
| 13900020 | Invalid argument |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900034 | Operation would block |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## write

```TypeScript
declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options: WriteOptions,
  callback: AsyncCallback<number>
): void
```

将数据写入文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options: WriteOptions,
  callback: AsyncCallback<number>
): void--><!--Device-unnamed-declare function write(
  fd: number,
  buffer: ArrayBuffer | string,
  options: WriteOptions,
  callback: AsyncCallback<number>
): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](arkts-corefile-file-fs-writeoptions-i.md) | 是 | 支持如下选项：<br/>- offset，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>- length，number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'。当前仅支持?'utf-8'。<br>**起始版本：** 11 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 异步将数据写入完成后执行的回调函数。返回实际写入的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900013 | Bad address |
| 13900020 | Invalid argument |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900034 | Operation would block |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

