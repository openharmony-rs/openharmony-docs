# FileSync

����ͬ����������֧���ļ�������Ӧ����������ļ��Ķ���ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���FileSyncʵ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## constructor

```TypeScript
constructor()
```

����ͬ�����̵Ĺ��캯�������ڻ�ȡFileSync���ʵ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync()

```

## getLastSyncTime

```TypeScript
getLastSyncTime(): Promise<number>
```

�첽������ȡ�ϴ�ͬ��ʱ�䡣ʹ��Promise�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬷����ϴ�ͬ��ʱ�䡣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.getLastSyncTime().then((timeStamp: number) => {
  let date = new Date(timeStamp);
  console.info("get last sync time successfully: "+ date);
}).catch((err: BusinessError) => {
  console.error("get last sync time failed with error message: " + err.message + ", error code: " + err.code);
});


```

## getLastSyncTime

```TypeScript
getLastSyncTime(callback: AsyncCallback<number>): void
```

��ȡ�ϴ�ͬ��ʱ�䡣ʹ��callback�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;number&gt; | 是 | �ص��������첽��ȡ�ϴ�ͬ��ʱ�䡣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.getLastSyncTime((err: BusinessError, timeStamp: number) => {
  if (err) {
    console.error("get last sync time with error message: " + err.message + ", error code: " + err.code);
  } else {
    let date = new Date(timeStamp);
    console.info("get last sync time successfully: "+ date);
  }
});

```

## off

```TypeScript
off(event: 'progress', callback?: Callback<SyncProgress>): void
```

����ͬ�������Ƴ�'progress'���͵�ָ��callback�ص���

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | Callback&lt;SyncProgress&gt; | 否 | �ص�������ͬ�������¼��� Ĭ��ֵΪnull�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("file sync state: " + pg.state + "error type: " + pg.error);
}

fileSync.on('progress', callback);

fileSync.off('progress', callback);

```

## on

```TypeScript
on(event: 'progress', callback: Callback<SyncProgress>): void
```

����ͬ����������ͬ�������¼�������

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'progress' | 是 | ���ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | Callback&lt;SyncProgress&gt; | 是 | �ص�������ͬ�������¼��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let fileSync = new cloudSync.FileSync();
let callback = (pg: cloudSync.SyncProgress) => {
  console.info("file sync state: " + pg.state + "error type: " + pg.error);
}

fileSync.on('progress', callback);

```

## start

```TypeScript
start(): Promise<void>
```

�첽�����������̶���ͬ����ʹ��Promise�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [22400001](../../errorcode-universal.md#22400001-Cloud) | Cloud status not ready. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400003](../../errorcode-universal.md#22400003-Low) | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("file sync state: " + pg.state + "error type: " + pg.error);
}

fileSync.on('progress', callback);

fileSync.start().then(() => {
  console.info("start sync successfully");
}).catch((err: BusinessError) => {
  console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

�첽�����������̶���ͬ����ʹ��callback�첽�ص���

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽��������ͬ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [22400001](../../errorcode-universal.md#22400001-Cloud) | Cloud status not ready. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400003](../../errorcode-universal.md#22400003-Low) | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.start((err: BusinessError) => {
  if (err) {
    console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start sync successfully");
  }
});

```

## stop

```TypeScript
stop(): Promise<void>
```

�첽����ֹͣ���̶���ͬ����ʹ��Promise�첽�ص���

����stop�ӿڣ�ͬ�����̻�ֹͣ���ٴε���[start](arkts-corefile-cloudsync-filesync-c.md#start-1)�ӿڻ����ͬ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

�첽����ֹͣ���̶���ͬ����ʹ��callback�첽�ص���

����stop�ӿڣ�ͬ�����̻�ֹͣ���ٴε���[start](arkts-corefile-cloudsync-filesync-c.md#start-1)�ӿڻ����ͬ����

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽ֹͣ����ͬ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let fileSync = new cloudSync.FileSync();

fileSync.stop((err: BusinessError) => {
  if (err) {
    console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop sync successfully");
  }
});

```

