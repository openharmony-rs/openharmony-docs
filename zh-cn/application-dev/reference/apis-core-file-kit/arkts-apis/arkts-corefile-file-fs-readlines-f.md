# readLines

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## readLines

```TypeScript
declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>
```

逐行读取文件文本内容，只支持读取utf-8格式文件。使用promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [Options](arkts-corefile-file-fs-options-i.md) | 否 | 可选项。支持以下选项：   - encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | Promise对象。返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Options } from '@kit.CoreFileKit';

let filePath = pathDir + "/test.txt";
let options: Options = {
  encoding: 'utf-8'
};
fileIo.readLines(filePath, options).then((readerIterator: fileIo.ReaderIterator) => {
  for (let it = readerIterator.next(); !it.done; it = readerIterator.next()) {
    console.info(`Succeeded in reading lines, content: ${it.value}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to read lines. Code: ${err.code}, message: ${err.message}`);
});
```


## readLines

```TypeScript
declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void
```

逐行读取文件文本内容，只支持读取utf-8格式文件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | 是 | 回调函数，返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
fileIo.readLines(filePath, (err: BusinessError, readerIterator: fileIo.ReaderIterator) => {
  if (err) {
    console.error(`Failed to read lines. Code: ${err.code}, message: ${err.message}`);
  } else {
    for (let it = readerIterator.next(); !it.done; it = readerIterator.next()) {
      console.info(`Succeeded in reading lines, content: ${it.value}`);
    }
  }
});
```


## readLines

```TypeScript
declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void
```

逐行读取文件文本内容，可配置读取选项，只支持读取utf-8格式文件。使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | [Options](arkts-corefile-file-fs-options-i.md) | 是 | 可选项。支持以下选项：   - encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8'。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | 是 | 回调函数，返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Options } from '@kit.CoreFileKit';

let filePath = pathDir + "/test.txt";
let options: Options = {
  encoding: 'utf-8'
};
fileIo.readLines(filePath, options, (err: BusinessError, readerIterator: fileIo.ReaderIterator) => {
  if (err) {
    console.error(`Failed to read lines. Code: ${err.code}, message: ${err.message}`);
  } else {
    for (let it = readerIterator.next(); !it.done; it = readerIterator.next()) {
      console.info(`Succeeded in reading lines, content: ${it.value}`);
    }
  }
});
```
