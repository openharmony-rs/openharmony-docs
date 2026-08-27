# stat

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## stat

```TypeScript
declare function stat(file: string | number): Promise<Stat>
```

获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件或目录的应用沙箱路径path、URI或已打开的文件描述符fd。   **说明：**从API version 22开始，支持传入URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | Promise对象。返回文件或目录的具体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too number |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
fileIo.stat(filePath).then((stat: fileIo.Stat) => {
  console.info(`Succeeded in getting file info, the size of file is ${stat.size}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get file info. Code: ${err.code}, message: ${err.message}`);
});
```


## stat

```TypeScript
declare function stat(file: string | number, callback: AsyncCallback<Stat>): void
```

获取文件或目录的详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件或目录的应用沙箱路径path、URI或已打开的文件描述符fd。   **说明：**从API version 22开始，支持传入URI。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | 是 | 异步获取文件或目录的信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too number |
| 13900031 | Function not implemented |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

fileIo.stat(pathDir, (err: BusinessError, stat: fileIo.Stat) => {
  if (err) {
    console.error(`Failed to get file info. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting file info, the size of file is ${stat.size}`);
  }
});
```
