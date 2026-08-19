# FileUri

FileUri表示文件的URI，继承自uri.URI。

**继承/实现关系：** FileUri extends uri.URI

**起始版本：** 23

<!--Device-fileUri-class FileUri--><!--Device-fileUri-class FileUri-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

## 导入模块

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor(uriOrPath: string)
```

FileUri的构造函数，用于创建FileUri实例。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FileUri-constructor(uriOrPath: string)--><!--Device-FileUri-constructor(uriOrPath: string)-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriOrPath | string | 是 | URI或路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 14300002 | Invalid uri |
| 13900042 | Unknown error |

**示例**

```TypeScript
let pathDir = this.context.filesDir; // 获取应用沙箱路径。
let path = pathDir + '/test';
let uri = fileUri.getUriFromPath(path);  // file://<packageName>/data/storage/el2/base/haps/entry/files/test
let fileUriObject = new fileUri.FileUri(uri);
console.info(`The name of FileUri is ${fileUriObject.name}`);
```

## getFullDirectoryUri

```TypeScript
getFullDirectoryUri(): string
```

获取当前文件URI所在路径的完整目录URI。URI指向目录时直接返回原URI。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FileUri-getFullDirectoryUri(): string--><!--Device-FileUri-getFullDirectoryUri(): string-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回文件所在路径的目录URI；URI指向目录时返回当前URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let pathDir = this.context.filesDir; // 获取应用沙箱路径。
  let path = pathDir + '/test.txt';
  let fileUriObject = new fileUri.FileUri(path);
  let directoryUri = fileUriObject.getFullDirectoryUri();
  console.info(`success to getFullDirectoryUri: ${JSON.stringify(directoryUri)}`);
} catch (error) {
  console.error(`failed to getFullDirectoryUri because: ${JSON.stringify(error)}`);
}
```

## isRemoteUri

```TypeScript
isRemoteUri(): boolean
```

判断当前URI是否为包含远端标识networkid的远端URI。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FileUri-isRemoteUri(): boolean--><!--Device-FileUri-isRemoteUri(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示远端URI，返回false表示本地URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900042 | Unknown error |

**示例**

```TypeScript
function isRemoteUriExample() {
  let uri = 'file://com.example.demo/data/storage/el2/base/test.txt?networkid=xxxx'; // ?networkid设备id，远端URI的标识
  let fileUriObject = new fileUri.FileUri(uri);
  let ret = fileUriObject.isRemoteUri();
  if (ret) {
    console.info('It is a remote URI.');
  }
}
```

## toString

```TypeScript
toString(): string
```

将当前URI转换为序列化字符串。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-toString(): string--><!--Device-FileUri-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字符串类型的URI。 |

