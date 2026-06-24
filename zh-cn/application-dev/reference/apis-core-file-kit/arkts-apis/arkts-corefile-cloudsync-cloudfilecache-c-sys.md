# CloudFileCache

�����ļ������������֧���ļ�����Ӧ��ԭ�ļ��������̡�

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## cleanCache

```TypeScript
cleanCache(uri: string): void
```

ͬ������ɾ���ļ����档

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ��ɾ�������ļ���uri�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanCache(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("clean cache failed with error message: " + err.message + ", error code: " + err.code);
} 


```

## constructor

```TypeScript
constructor(bundleName: string)
```

A constructor used to create a CloudFileCache object.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Name of the bundle that need to start download task and subscribes download<br/>progress. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |

**示例：**

```TypeScript
let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");

```

## getDownloadList

```TypeScript
getDownloadList(uris: Array<string>): Promise<Array<DownloadProgress>>
```

��ȡ�ļ����ؽ����б���ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | ����ѯ���ؽ��ȵ��ļ�URI���飬���鳤��ȡֵ��Χ[1,100]�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DownloadProgress&gt;&gt; | - Promise���󣬷����ļ����ؽ����б��Ľ���� |

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
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path1 = "/data/storage/el2/cloud/1.txt";
let path2 = "/data/storage/el2/cloud/2.txt";
let uri1 = fileUri.getUriFromPath(path1);
let uri2 = fileUri.getUriFromPath(path2);
let uriArray = [uri1, uri2];

try {
  fileCache.getDownloadList(uriArray).then((downloadList: Array<cloudSync.DownloadProgress>) => {
    console.info("get download list successfully");
    for (let i = 0; i < downloadList.length; i++) {
      console.info("download progress - uri: ".concat(downloadList[i].uri, ", state: ").concat(downloadList[i].state.toString()));
      console.info("processed: ".concat(downloadList[i].processed.toString(), ", size: ").concat(downloadList[i].size.toString()));
      console.info("error: ".concat(downloadList[i].error.toString()));
    }
  }).catch((error: BusinessError) => {
    console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
}

```

