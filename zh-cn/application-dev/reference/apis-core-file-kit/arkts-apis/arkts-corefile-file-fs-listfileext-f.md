# listFileExt

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## listFileExt

```TypeScript
declare function listFileExt(
  path: string,
  options?: ListFileExtOptions
): Promise<string[]>
```

列出目录下所有文件名，支持递归列出和自定义文件名过滤。使用Promise异步回调。可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | [ListFileExtOptions](arkts-corefile-file-fs-listfileextoptions-i.md) | 否 | 文件列出选项。默认为空，表示不递归、不限制列出数量、不进行过滤。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string[] & gt; | Promise used to return the file names listed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo, ListFileExtOptions, FileFilter } from '@kit.CoreFileKit';

let filter: FileFilter = {
  filter: (name: string): boolean => {
    return name.endsWith('.txt');
  }
};
let options: ListFileExtOptions = {
  recursion: false,
  listNum: 0,
  fileFilter: filter
};
fileIo.listFileExt(pathDir, options).then((filenames: Array<string>) => {
  console.info(`Succeeded in listing file.`);
  for (let i = 0; i < filenames.length; i++) {
    console.info(`Succeeded in listing file, file name: ${filenames[i]}`);
  }
}).catch((error: Error) => {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to list file. Code: ${err.code}, message: ${err.message}`);
});
```
