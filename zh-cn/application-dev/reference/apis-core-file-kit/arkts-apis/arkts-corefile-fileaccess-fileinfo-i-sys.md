# FileInfo（系统接口）

表示文件(夹)属性信息和接口能力。

**起始版本：** 9

**废弃版本：** 23

<!--Device-fileAccess-interface FileInfo--><!--Device-fileAccess-interface FileInfo-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

<a id="listfile"></a>
## listFile

```TypeScript
listFile(filter?: Filter): FileIterator
```

以同步方法从某个目录，基于过滤器，获取下一级符合条件的文件(夹)信息的迭代器对象FileIterator，然后通过[next](arkts-corefile-fileaccess-fileiterator-i-sys.md#next-1)方法返回[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)。目前仅支持内置存储设备过滤，外置存储设备不支持过滤。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** listFile

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-listFile(filter?: Filter): FileIterator--><!--Device-FileInfo-listFile(filter?: Filter): FileIterator-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-arkui/arkts-components/arkts-arkui-filter-t.md) | 否 | Indicates the filter of file. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileIterator](arkts-corefile-fileaccess-fileiterator-i-sys.md) | Returns the FileIterator Object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// fileInfoDir 表示某个目录信息
// let filter = { suffix : [".txt", ".jpg", ".xlsx"] };
let fileInfoDir :Array<fileAccess.FileInfo> = [];
let subfileInfos: Array<fileAccess.FileInfo> = [];
let isDone: boolean = false;
try {
  for (let i = 0; i < fileInfoDir.length; ++i) {
    let fileIterator = fileInfoDir[i].listFile();
    // 含过滤器实现的listFile
    // let fileIterator = fileInfoDir.listFile(filter);
    if (!fileIterator) {
      console.error("listFile interface returns an undefined object");
    }
    while (!isDone) {
      let result = fileIterator.next();
      console.info("next result = " + JSON.stringify(result));
      isDone = result.done;
      if (!isDone) {
        subfileInfos.push(result.value);
      }
    }
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("listFile failed, errCode:" + error.code + ", errMessage:" + error.message);
}

```

<a id="scanfile"></a>
## scanFile

```TypeScript
scanFile(filter?: Filter): FileIterator
```

以同步方法从某个目录，基于过滤器，递归获取符合条件的文件信息的迭代器对象FileIterator，然后通过[next](arkts-corefile-fileaccess-fileiterator-i-sys.md#next-1)方法返回[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)。目前仅支持内置存储设备。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-scanFile(filter?: Filter): FileIterator--><!--Device-FileInfo-scanFile(filter?: Filter): FileIterator-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [Filter](../../apis-arkui/arkts-components/arkts-arkui-filter-t.md) | 否 | Indicates the filter of file. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileIterator](arkts-corefile-fileaccess-fileiterator-i-sys.md) | Returns the FileIterator Object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// fileInfoDir 表示某个目录信息
// let filter = {suffix : [".txt", ".jpg", ".xlsx"]};
let fileInfoDir: Array<fileAccess.FileInfo> = [];
let subfileInfos: Array<fileAccess.FileInfo> = [];
let isDone: boolean = false;
try {
  for (let i = 0; i < fileInfoDir.length; ++i) {
    let fileIterator = fileInfoDir[i].scanFile();
    // 含过滤器实现的scanFile
    // let fileIterator = fileInfoDir.scanFile(filter);
    if (!fileIterator) {
      console.error("scanFile interface returns an undefined object");
    }
    while (!isDone) {
      let result = fileIterator.next();
      console.info("next result = " + JSON.stringify(result));
      isDone = result.done;
      if (!isDone) {
        subfileInfos.push(result.value);
      }
    }
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("scanFile failed, errCode:" + error.code + ", errMessage:" + error.message);
}

```

## fileName

```TypeScript
fileName: string
```

文件(夹)的名称。

**类型：** string

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-fileName: string--><!--Device-FileInfo-fileName: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## mimeType

```TypeScript
mimeType: string
```

文件(夹)的媒体资源类型。

**类型：** string

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-mimeType: string--><!--Device-FileInfo-mimeType: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: number
```

文件(夹)的权限信息。

**类型：** number

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-mode: number--><!--Device-FileInfo-mode: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## mtime

```TypeScript
mtime: number
```

文件(夹)的修改时间。自1970年1月1日起至目标时间的毫秒数。

**类型：** number

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-mtime: number--><!--Device-FileInfo-mtime: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## relativePath

```TypeScript
relativePath: string
```

文件(夹)的相对路径。

**类型：** string

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-relativePath: string--><!--Device-FileInfo-relativePath: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

文件(夹)的大小。（单位：字节）

**类型：** number

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-size: number--><!--Device-FileInfo-size: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

文件(夹)的uri。

**类型：** string

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-uri: string--><!--Device-FileInfo-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

