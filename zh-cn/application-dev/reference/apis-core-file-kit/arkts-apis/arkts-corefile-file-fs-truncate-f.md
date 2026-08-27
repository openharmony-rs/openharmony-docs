# truncate

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## truncate

```TypeScript
declare function truncate(file: string | number, len?: number): Promise<void>
```

截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let len: number = 5;
fileIo.truncate(filePath, len).then(() => {
  console.info(`Succeeded in truncating file.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to truncate file. Code: ${err.code}, message: ${err.message}`);
});
```


## truncate

```TypeScript
declare function truncate(file: string | number, callback: AsyncCallback<void>): void
```

截断文件，删除文件内容。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当截断文件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
fileIo.truncate(filePath, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to truncate. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in truncating.`);
  }
});
```


## truncate

```TypeScript
declare function truncate(file: string | number, len: number, callback: AsyncCallback<void>): void
```

截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。<br>**起始版本：** 11 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当截断文件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let len: number = 5;
fileIo.truncate(filePath, len, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to truncate. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in truncating.`);
  }
});
```
