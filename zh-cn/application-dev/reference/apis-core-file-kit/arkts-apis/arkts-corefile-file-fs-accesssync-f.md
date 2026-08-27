# accessSync

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## accessSync

```TypeScript
declare function accessSync(path: string, mode?: AccessModeType): boolean
```

以同步方法检查文件或目录是否存在，或校验操作权限。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| mode | [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | 否 | 文件或目录校验的权限。不填该参数则默认校验文件或目录是否存在。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true，表示文件或目录存在；返回false，表示文件或目录不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
try {
  let res = fileIo.accessSync(filePath);
  if (res) {
    console.info(`Succeeded in checking file, file exists.`);
  } else {
    console.info(`Succeeded in checking file, file does not exist.`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to accessSync. Code: ${err.code}, message: ${err.message}`);
}
```


## accessSync

```TypeScript
declare function accessSync(path: string, mode: AccessModeType, flag: AccessFlagType): boolean
```

以同步方法检查文件或目录是否在本地，或校验操作权限。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| mode | [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | 是 | 文件或目录校验的权限。 |
| flag | [AccessFlagType](arkts-corefile-file-fs-accessflagtype-e.md) | 是 | 文件或目录校验的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true，表示文件或目录在本地且校验权限存在；返回false，表示文件或目录不存在或者文件或目录在云端或其他分布式设备上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900030 | File name too number |
| 13900033 | Too many symbolic links encountered |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
try {
  let res = fileIo.accessSync(filePath, fileIo.AccessModeType.EXIST, fileIo.AccessFlagType.LOCAL);
  if (res) {
    console.info(`Succeeded in checking file, file exists.`);
  } else {
    console.info(`Succeeded in checking file, file does not exist.`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to accessSync. Code: ${err.code}, message: ${err.message}`);
}
```
