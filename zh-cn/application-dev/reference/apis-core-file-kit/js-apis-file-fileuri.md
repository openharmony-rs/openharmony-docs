# @ohos.file.fileuri (文件URI)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie-->
<!--Designer: @wang_zhangjun; @chenxi0605-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

该模块提供通过PATH获取文件统一资源标志符（Uniform Resource Identifier，URI），后续可通过使用[@ohos.file.fs](js-apis-file-fs.md)进行相关open、read、write等操作，实现文件分享。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { fileUri } from '@kit.CoreFileKit';
```

使用该功能模块前，需要先获取其应用沙箱路径，开发示例如下：

  ```ts
  import { UIAbility } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';

  export default class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
      let context = this.context;
      let pathDir = context.filesDir;
    }
  }
  ```

## FileUri<sup>10+</sup>

### 属性

**系统能力**：SystemCapability.FileManagement.AppFileService

| 名称 | 类型 | 必填 | 说明|
| -------- | --------| -------- |----------------|
| path<sup>10+</sup> | string | 是 | 将uri转换成对应的沙箱路径path。 1、uri转path过程中会将uri中存在的ASCII码进行解码后拼接在原处，非系统接口生成的uri中可能存在ASCII码解析范围之外的字符，导致字符串无法正常拼接；2、转换处理为系统约定的字符串替换规则（规则随系统演进可能会发生变化），转换过程中不进行路径校验操作，无法保证转换结果的一定可以访问。 |
| name<sup>10+</sup> | string | 是 | 通过传入的uri获取到对应的文件名称。（如果文件名中存在ASCII码将会被解码处理后拼接在原处）<br>**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。|

### constructor<sup>10+</sup>

constructor(uriOrPath: string)

constructor是FileUri的构造函数。

**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.AppFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明|
| -------- | -------- | -------- |--------|
| uriOrPath | string | 是 | URI或路径。URI类型：<br/>-&nbsp; 应用沙箱URI：file://\<bundleName>/\<sandboxPath> <br/>-&nbsp; 公共目录文件类URI：file://docs/storage/Users/currentUser/\<publicPath> <br/>-&nbsp; 公共目录媒体类URI：file://media/\<mediaType>/IMG_DATATIME_ID/\<displayName> |

**错误码：**

以下错误码的详细介绍请参见[文件管理子系统错误码](errorcode-filemanagement.md)。
| 错误码ID| 错误信息        |
| -------- | ---------- |
| 13900005 | I/O error |
| 13900042 | Unknown error |
| 13900020 | Invalid argument |
| 14300002 | Invalid uri |

**示例：**

  ```ts
  let path = pathDir + '/test';
  let uri = fileUri.getUriFromPath(path);  // file://<packageName>/data/storage/el2/base/haps/entry/files/test
  let fileUriObject = new fileUri.FileUri(uri);
  console.info("The name of FileUri is " + fileUriObject.name);
  ```

### toString<sup>10+</sup>

toString(): string

**系统能力**：SystemCapability.FileManagement.AppFileService

返回字符串类型URI。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 返回字符串类型URI。 |

**示例：**

  ```ts
  let path = pathDir + '/test';
  let fileUriObject = new fileUri.FileUri(path);
  console.info("The uri of FileUri is " + fileUriObject.toString());
  ```

### getFullDirectoryUri<sup>11+</sup>

getFullDirectoryUri(): string

获取所在路径URI。URI指向文件则返回所在路径的URI，URI指向目录则不处理直接返回原串；URI指向的文件不存在或属性获取失败则返回空串。

如果当前FileUri指向文件，将返回文件所在路径URI。如`xxx/example.txt`，将返回`xxx`。

如果当前FileUri指向目录，将返回当前路径的URI。

**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.AppFileService

**返回值：**

| 类型| 说明|
| --------- |--------|
| string | 获取所在路径URI，文件获取所在路径URI，目录获取当前路径URI。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理子系统错误码](errorcode-filemanagement.md)。

| 错误码ID| 错误信息|
| -------- |--------|
| 13900002 | No such file or directory |
| 13900012 | Permission denied         |
| 13900042 | Unknown error             |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  try {
    let path = pathDir + '/test.txt';
    let fileUriObject = new fileUri.FileUri(path);
    let directoryUri = fileUriObject.getFullDirectoryUri();
    console.log(`success to getFullDirectoryUri: ${JSON.stringify(directoryUri)}`);
  } catch (error) {
    console.error(`failed to getFullDirectoryUri because: ${JSON.stringify(error)}`);
  }
  ```

### isRemoteUri<sup>12+</sup>

isRemoteUri(): boolean

判断当前URI是否是远端URI。

**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.AppFileService

**返回值：**

| 类型| 说明|
| -------- |---------|
| boolean | - 返回true，表示当前FileUri指向远端文件或目录，如`xxx/example.txt?networkid=xxx`。<br>- 返回false，表示当前FileUri指向本地的文件或目录。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理子系统错误码](errorcode-filemanagement.md)。

| 错误码ID| 错误信息|
| --------- |--------|
| 13900042 | Unknown error|

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  function isRemoteUriExample() {
    let uri = "file://com.example.demo/data/stroage/el2/base/test.txt?networkid=xxxx";//?networkid设备id，远端URI的标识
    let fileUriObject = new fileUri.FileUri(uri);
    let ret = fileUriObject.isRemoteUri();
    if (ret) {
        console.log(`It is a remote uri.`);
    }
  }
  ```

## fileUri.getUriFromPath

getUriFromPath(path: string): string

通过传入的路径path生成应用自己的URI；将path转URI时，路径中的中文及非数字字母的特殊字符将会被编译成对应的ASCII码，拼接在URI中。

**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.FileManagement.AppFileService

**参数：**

| 参数名 | 类型   | 必填 | 说明|
| ------ | ------ | ---- | ------- |
| path   | string | 是   | 文件的沙箱路径。 |

**返回值：**

  | 类型 | 说明|
  | ------- |------|
  | string | 通过传入的路径path生成应用自己的URI；将path转URI时，路径中的中文及非数字字母的特殊字符将会被编译成对应的ASCII码，拼接在URI中。 |

**错误码：**  

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。
| 错误码ID| 错误信息        |
| ---------- | ---------- |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types |

**示例：**

  ```ts
  let filePath = pathDir + "/test";
  let uri = fileUri.getUriFromPath(filePath);
  ```