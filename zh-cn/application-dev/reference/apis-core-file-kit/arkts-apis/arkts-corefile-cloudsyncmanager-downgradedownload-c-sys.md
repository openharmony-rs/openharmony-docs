# DowngradeDownload（系统接口）

ȫ�����أ�Ϊ���̹���Ӧ���ṩ���������ƶ����ݵ�������

����ȫ�����ض�������֧�����̹���Ӧ����������ļ���ȫ���������̡�

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(bundleName: string)
```

ȫ�����ض���Ĺ��캯�������ڻ�ȡָ��������DowngradeDownload���ʵ����

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ�ð����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.demo.a';
try {
  let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to create downgrade manager object, error code: ${error.code}, message: ${error.message}`);
}

```

## getCloudFileInfo

```TypeScript
getCloudFileInfo(): Promise<CloudFileInfo>
```

��ȡ��Ҫȫ�����ص�Ӧ�ý�λ�ڱ��ء���λ���ƶ˻��߱��غ��ƶ˾��е��ļ���С�͸�����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CloudFileInfo&gt; | Promise���󣬷���Я���������ƶ��ļ���Ϣ�Ķ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.getCloudFileInfo().then((fileInfo: cloudSyncManager.CloudFileInfo) => {
  console.info("cloud file info: " + JSON.stringify(fileInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to get downgrade info, error message: ${err.message}, error code: ${err.code}`);
});

```

## startDownload

```TypeScript
startDownload(callback: Callback<DownloadProgress>): Promise<void>
```

����ָ��Ӧ�õ����ļ���ȫ�����أ�ʹ��Promise�첽�ص���ʹ��callback�첽�ص���

ͬһӦ�ô�������ִ�е�ȫ���������������£��ظ������᷵�ش�����Ϣ��22400006����

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;DownloadProgress&gt; | 是 | �ص�������ȫ�����ؽ��ȣ�����ΪDownloadProgress������ֵΪvoid�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| [22400006](../../errorcode-universal.md#22400006-The) | The same task is already in progress. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
let callback = (data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSyncManager.DownloadState.COMPLETED) {
    console.info('Downgrade finished.');
  } else if (data.state == cloudSyncManager.DownloadState.STOPPED) {
    console.info(`Downgrade stopped, reason: ${data.stopReason}.`);
  }
};
downgradeMgr.startDownload(callback).then(() => {
  console.info("Downgrade started successfully.");
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});

```

## startTransfer

```TypeScript
startTransfer(targetUri: string, callback: Callback<TransferProgress>): void
```

������Ŀ¼������ɱ������ص��ļ���Ǩ��ָ��Ŀ¼��������ͨ���ص��ϱ���Ǩ���ȡ�ʹ��callback�첽�ص���

ͬһӦ�ô�������ִ�еİ�Ǩ���������£��ظ������᷵�ش�����Ϣ��22400006����

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetUri | string | 是 | ���ڴ�Ű�Ǩ����ļ�·��URI�������ԡ�/file://docs/storage/Users/currentUser/��Ϊǰ׺�� |
| callback | Callback&lt;TransferProgress&gt; | 是 | �ص����������ذ�Ǩ���ȡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted. Possible causes:<br/><br/>1.The DowngradeDownload task is running.<br/><br/>2.The full data synchronization task is running. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified.<br/><br/>2.The length of the input uri does not meet the value range requirement.<br/><br/>3.The input uri does not belong to a File Manager public directory. |
| [22400006](../../errorcode-universal.md#22400006-The) | The same task is already in progress. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetPath: string = "file://docs/storage/Users/currentUser/Download/";
try {
    let downgradeMgr = new cloudSyncManager.DowngradeDownload("com.demo");
    downgradeMgr.startTransfer(targetPath, (data: cloudSyncManager.TransferProgress) => {
        console.info(`Transfer progress: successfulCount: ${data.successfulCount}, totalCount: ${data.totalCount}`);
    });
} catch (err) {
    let e = err as BusinessError;
    console.error("transfer files failed with error message: " + e.message + ", error code: " + e.code);
}

```

## stopDownload

```TypeScript
stopDownload(): Promise<void>
```

ֹͣ��[startDownload](arkts-corefile-cloudsyncmanager-downgradedownload-c-sys.md#startDownload-1)������ȫ����������ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application<br/>uses system API. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.startDownload((data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
}).then(() => {
  console.info("Downgrade started successfully.");
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});

let needStop = true;
if (needStop) {
  downgradeMgr.stopDownload().then(() => {
    console.info("Downgrade stopped successfully.");
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop downgrade, error message: ${err.message}, error code: ${err.code}`);
  });
}

```

