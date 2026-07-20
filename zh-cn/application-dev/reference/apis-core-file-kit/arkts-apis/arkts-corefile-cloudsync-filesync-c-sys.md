# FileSync

云盘同步对象，用于支撑文件管理器应用完成云盘文件的端云同步流程。在使用前，需要先创建FileSync实例。

**起始版本：** 12

<!--Device-cloudSync-class FileSync--><!--Device-cloudSync-class FileSync-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(bundleName: string)
```

端云同步流程的构造函数，用于获取FileSync类的实例。

**起始版本：** 12

<!--Device-FileSync-constructor(bundleName: string)--><!--Device-FileSync-constructor(bundleName: string)-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync("com.ohos.demo")

```

<a id="getuploadlist"></a>
## getUploadList

```TypeScript
getUploadList(uris: Array<string>): Promise<Array<UploadProgress>>
```

获取文件上传列表和进度信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSync-getUploadList(uris: Array<string>): Promise<Array<UploadProgress>>--><!--Device-FileSync-getUploadList(uris: Array<string>): Promise<Array<UploadProgress>>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | 待查询上传进度的文件URI数组，数组长度取值范围[1,100]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;UploadProgress&gt;&gt; | - Promise对象，返回上传进度信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit.<br>3.The input parameter contains an invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let uris: string[] = ["file:///data/storage/el2/cloud/1.txt", "file:///data/storage/el2/cloud/2.jpg"];

fileSync.getUploadList(uris).then((progressList: cloudSync.UploadProgress[]) => {
  console.info("get upload list successfully, count: " + progressList.length);
  for (let i = 0; i < progressList.length; i++) {
    console.info("file uri: " + progressList[i].uri + ", state: " + progressList[i].state);
  }
}).catch((error: BusinessError) => {
  console.error("get upload list failed with error message: " + error.message + ", error code: " + error.code);
});

```

<a id="pauseupload"></a>
## pauseUpload

```TypeScript
pauseUpload(uri: string): void
```

暂停云文件上传。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSync-pauseUpload(uri: string): void--><!--Device-FileSync-pauseUpload(uri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待暂停的文件URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileSync.pauseUpload(uri);
  console.info("pause upload successfully.");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("pause upload failed with error message: " + error.message + ", error code: " + error.code);
}

```

<a id="registeruploadprogress"></a>
## registerUploadProgress

```TypeScript
registerUploadProgress(callback: Callback<UploadProgress>): void
```

注册上传进度回调函数，用于监听文件上传进度变化。使用callback异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSync-registerUploadProgress(callback: Callback<UploadProgress>): void--><!--Device-FileSync-registerUploadProgress(callback: Callback<UploadProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;UploadProgress&gt; | 是 | 回调函数，监听文件上传进度变化。当文件上传进度发生变化时触发回调，返回上传进度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameter are left unspecified.<br>2.The number of instances registered at the same time exceeds the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");

try {
  fileSync.registerUploadProgress((progress: cloudSync.UploadProgress) => {
    console.info(`upload progress - uri: ${progress.uri}, state: ${progress.state}`);
    console.info(`processed: ${progress.processed}, size: ${progress.size}`);
    console.info(`error: ${progress.error}`);
  });
  console.info("register upload progress successfully");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`register upload progress failed with error message: ${error.message}, error code: ${error.code}`);
}

```

<a id="resumeupload"></a>
## resumeUpload

```TypeScript
resumeUpload(uri: string): void
```

恢复云文件上传。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSync-resumeUpload(uri: string): void--><!--Device-FileSync-resumeUpload(uri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待恢复上传的文件URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileSync.resumeUpload(uri);
  console.info("resume upload successfully.");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("resume upload failed with error message: " + error.message + ", error code: " + error.code);
}

```

<a id="unregisteruploadprogress"></a>
## unregisterUploadProgress

```TypeScript
unregisterUploadProgress(): void
```

取消注册上传进度回调函数。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileSync-unregisterUploadProgress(): void--><!--Device-FileSync-unregisterUploadProgress(): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900010 | Try again. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");

try {
  fileSync.unregisterUploadProgress();
  console.info("unregister upload progress successfully");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("unregister upload progress failed with error message: " + error.message + ", error code: " + error.code);
}

```

