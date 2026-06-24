# FileSync

����ͬ����������֧���ļ�������Ӧ����������ļ��Ķ���ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���FileSyncʵ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## constructor

```TypeScript
constructor(bundleName: string)
```

����ͬ�����̵Ĺ��캯�������ڻ�ȡFileSync���ʵ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ�ð����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync("com.ohos.demo")

```

## getUploadList

```TypeScript
getUploadList(uris: Array<string>): Promise<Array<UploadProgress>>
```

��ȡ�ļ��ϴ��б��ͽ�����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | ����ѯ�ϴ����ȵ��ļ�URI���飬���鳤��ȡֵ��Χ[1,100]�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;UploadProgress&gt;&gt; | - Promise���󣬷����ϴ�������Ϣ���顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit.<br/><br/>3.The input parameter contains an invalid uri. |

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

## pauseUpload

```TypeScript
pauseUpload(uri: string): void
```

��ͣ���ļ��ϴ���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ����ͣ���ļ�URI�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

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

## registerUploadProgress

```TypeScript
registerUploadProgress(callback: Callback<UploadProgress>): void
```

ע���ϴ����Ȼص����������ڼ����ļ��ϴ����ȱ仯��ʹ��callback�첽�ص���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;UploadProgress&gt; | 是 | �ص������������ļ��ϴ����ȱ仯�����ļ��ϴ����ȷ����仯ʱ�����ص��������ϴ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameter are left unspecified.<br/><br/>2.The number of instances registered at the same time exceeds the upper limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync("com.ohos.demo");

try {
  fileSync.registerUploadProgress((progress: cloudSync.UploadProgress) => {
    console.info("upload progress - uri: " + progress.uri + ", state: " + progress.state);
    console.info("processed: " + progress.processed + ", size: " + progress.size);
    console.info("error: " + progress.error);
  });
  console.info("register upload progress successfully");
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("register upload progress failed with error message: " + error.message + ", error code: " + error.code);
}

```

## resumeUpload

```TypeScript
resumeUpload(uri: string): void
```

�ָ����ļ��ϴ���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ���ָ��ϴ����ļ�URI�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

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

## unregisterUploadProgress

```TypeScript
unregisterUploadProgress(): void
```

ȡ��ע���ϴ����Ȼص�������

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |

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

