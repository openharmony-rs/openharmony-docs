# CloudFileCache

�����ļ������������֧���ļ�����Ӧ��ԭ�ļ��������̡�

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## cleanFileCache

```TypeScript
cleanFileCache(uri: string): void
```

ͬ������ɾ���ļ����档

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ��ɾ�������ļ���URI�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanFileCache(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("clean file cache failed with error message: " + err.message + ", error code: " + err.code);
}


```

## cleanFileCache

```TypeScript
cleanFileCache(): Promise<void>
```

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Return Promise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();

fileCache.cleanFileCache().then(() => {
  console.info("clean file cache successfully");
}).catch((err: BusinessError) => {
  console.error("clean file cache failed with error message: " + err.message + ", error code: " + err.code);
});


```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **CloudFileCache** instance. Data is not shared between multiple instances.

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

**示例：**

```TypeScript
let fileCache = new cloudSync.CloudFileCache();

```

## getCachedTotalSize

```TypeScript
getCachedTotalSize(): Promise<number>
```

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | - Return the total size of cached files. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();

fileCache.getCachedTotalSize().then((totalDownloadSize: number) => {
  console.info("totalDownloadSize: " + totalDownloadSize);
}).catch((err: BusinessError) => {
  console.error("get totalDownloadSize failed with error message: " + err.message + ", error code: " + err.code);
});


```

## off

```TypeScript
off(event: 'progress', callback?: Callback<DownloadProgress>): void
```

�����ļ���������Ƴ�'progress'���͵�ָ��callback�ص���

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | Callback&lt;DownloadProgress&gt; | 否 | �ص����������ļ����ع����¼�������д������Ϊȡ��ָ���Ļص�����������Ϊȡ����ǰ���ĵ����лص������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

try {
  fileCache.on('progress', callback);
  fileCache.off('progress', callback);
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

```

## off

```TypeScript
off(event: 'batchDownload', callback?: Callback<MultiDownloadProgress>): void
```

�����ļ���������Ƴ���
[on](arkts-corefile-cloudsync-cloudfilecache-c.md#on-2)�ӿ����ӵ�����
��������������¼��ļ�����

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'batchDownload' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'batchDownload'����ʾ������������¼��� |
| callback | Callback&lt;MultiDownloadProgress&gt; | 否 | �ص����������ļ�������������¼��������д�˲�������ȡ��ָ���Ļص����������򣬽�ȡ����ǰ���ĵ���ͬ�¼����͵����л�<br/>�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.MultiDownloadProgress) => {
  console.info("download state: " + pg.state);
}

try {
  fileCache.on('batchDownload', callback);
  fileCache.off('batchDownload', callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}

```

## on

```TypeScript
on(event: 'progress', callback: Callback<DownloadProgress>): void
```

���������ļ���������¼�������

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | ���ĵ��¼����ͣ�ȡֵΪ'progress'�����ع����¼����� |
| callback | Callback&lt;DownloadProgress&gt; | 是 | �ص����������ļ����ع����¼��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
};

try {
  fileCache.on('progress', callback);
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

```

## on

```TypeScript
on(event: 'batchDownload', callback: Callback<MultiDownloadProgress>): void
```

�������ļ����������¼��ļ�����

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'batchDownload' | 是 | ���ĵ��¼����ͣ�ȡֵΪ'batchDownload'����ʾ������������¼��� |
| callback | Callback&lt;MultiDownloadProgress&gt; | 是 | �ص����������ļ�������������¼��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
let callback = (data: cloudSync.MultiDownloadProgress) => {
  console.info(`Batch download progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSync.State.COMPLETED) {
    console.info('Batch download finished.');
  } else if (data.state == cloudSync.State.FAILED) {
    console.info(`Batch download stopped, error type: ${data.errType}.`);
  }
};

try {
  fileCache.on('batchDownload', callback);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to register download callback, error code: ${error.code}, message: ${error.message}`);
}

```

## start

```TypeScript
start(uri: string): Promise<void>
```

�첽�������������ļ����档ʹ��Promise�첽�ص���

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
  });
} catch (e) {
  const error = e as BusinessError;
  console.error(`Error code: ${error.code}, message: ${error.message}`);
}

fileCache.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});

```

## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

�첽�������������ļ����档ʹ��callback�첽�ص���

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽�������ļ����ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileCache.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});

```

## startBatch

```TypeScript
startBatch(uris: Array<string>, fileType?: DownloadFileType): Promise<number>
```

�������ļ��������档ʹ��Promise�첽�ص���

��ͬ�����������������ͨ���ӿڷ��ص�����ID���֡�

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | URI�б���һ�ε������֧�ִ���400��URI����������22400004�� |
| fileType | DownloadFileType | 否 | �ļ����ͣ�Ĭ��ֵΪCONTENT���͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬷������������ļ��������������ID�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |
| [22400004](../../errorcode-universal.md#22400004-Exceed) | Exceed the maximum limit. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileCache = new cloudSync.CloudFileCache();
try {
  fileCache.on('batchDownload', (pg: cloudSync.MultiDownloadProgress) => {
    console.info(`batch download state: ${pg.state}`);
  });
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to unregister download callback, error code: ${error.code}, message: ${error.message}`);
}

let uriList: Array<string> = [];
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  console.info(`start batch download successfully, taskId: ${downloadId}`);
}).catch((err: BusinessError) => {
  console.error(`start download failed with error message: ${err.message}, error code: ${err.code}`);
});

```

## stop

```TypeScript
stop(uri: string, needClean?: boolean): Promise<void>
```

Stops downloading a file from the Drive Kit to the local device. This API uses a promise to return the result.

When **stop()** is called, the current file download process terminates, and downloaded files are retained by
default. You can call **start()** to resume the download.

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |
| needClean | boolean | 否 | �Ƿ�ɾ�������ص��ļ���Ĭ��ֵΪfalse��ʾ��ɾ����true��ʾɾ����<br/>��API version12��ʼ֧�ָò����� [since 12] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

fileCache.stop(uri, true).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});

```

## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

�첽����ֹͣ�����ļ����档ʹ��callback�첽�ص���

����stop�ӿڣ���ǰ�ļ��������̻���ֹ����ɾ�������ļ����ٴε���start�ӿ������������ء�

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽ֹͣ���ļ����ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

fileCache.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});

```

## stopBatch

```TypeScript
stopBatch(downloadId: number, needClean?: boolean): Promise<void>
```

ֹͣ��[startBatch](arkts-corefile-cloudsync-cloudfilecache-c.md#startBatch-1)���������ļ�������������ʹ��Promise�첽�ص���

����stopBatch�ӿڻ���ֹ��ǰ�ļ������������̣�δ������ɵĻ����ļ��Ƿ�ɾ����needClean����������

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| downloadId | number | 是 | ��Ҫֹͣ���������ID�� |
| needClean | boolean | 否 | �Ƿ�ɾ��δ��ɻ�����ļ���Ĭ��ֵΪfalse��ʾ��ɾ����true��ʾɾ���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let taskId = -1;
let uriList: Array<string> = [];
let fileCache = new cloudSync.CloudFileCache();
fileCache.startBatch(uriList, cloudSync.DownloadFileType.CONTENT).then((downloadId: number) => {
  taskId = downloadId;
  console.info("start batch download successfully");
}).catch((err: BusinessError) => {
  console.error(`start batch download failed with error message: ${err.message}, error code: ${err.code}`);
});

let needStop = true;
if (needStop && taskId > 0) {
  fileCache.stopBatch(taskId, true).then(() => {
    console.info("stop batch download successfully");
  }).catch((err: BusinessError) => {
    console.error(`stop batch download failed with error message: ${err.message}, error code: ${err.code}`);
  });
}

```

