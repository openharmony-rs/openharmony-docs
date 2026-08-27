# lstat

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## lstat

```TypeScript
declare function lstat(path: string): Promise<Stat>
```

获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径或URI。   **说明：**从API version 22开始，支持传入URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | Promise对象。返回Stat对象，表示文件的具体信息，详情见Stat。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/linkToFile";
fileIo.lstat(filePath).then((stat: fileIo.Stat) => {
  console.info(`Succeeded in getting symbolic link info, the size of file is ${stat.size}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get symbolic link info. Code: ${err.code}, message: ${err.message}`);
});
```


## lstat

```TypeScript
declare function lstat(path: string, callback: AsyncCallback<Stat>): void
```

获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径或URI。   **说明：**从API version 22开始，支持传入URI。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | 是 | 回调函数，返回Stat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/linkToFile";
fileIo.lstat(filePath, (err: BusinessError, stat: fileIo.Stat) => {
  if (err) {
    console.error(`Failed to get symbolic link info. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting symbolic link info, the size of file is ${stat.size}`);
  }
});
```
