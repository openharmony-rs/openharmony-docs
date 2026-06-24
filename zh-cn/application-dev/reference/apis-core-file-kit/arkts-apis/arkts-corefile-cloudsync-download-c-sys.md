# Download（系统接口）

���ļ����ض�������֧��ͼ��Ӧ��ԭͼ�ļ��������̡���ʹ��ǰ����Ҫ�ȴ���Downloadʵ����

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

���ļ��������̵Ĺ��캯�������ڻ�ȡDownload���ʵ����

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
let download = new cloudSync.Download()

```

## off

```TypeScript
off(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

��ͼ���ض����Ƴ�'progress'������ָ����callback�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | (pg: DownloadProgress) =&gt; void | 是 | �ص����������ļ����ع����¼������Ϊ<br/>[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md#DownloadProgress)������ֵΪvoid�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

let callback = (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
}

download.on('progress', callback);

download.off('progress', callback);

```

## off

```TypeScript
off(evt: 'progress'): void
```

��ͼ���ض����Ƴ�'progress'���͵����лص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'�����ع����¼����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
    console.info("download state: " + pg.state);
});

download.off('progress');

```

## on

```TypeScript
on(evt: 'progress', callback: (pg: DownloadProgress) => void): void
```

�������ļ����ع����¼�������

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ���ĵ��¼����ͣ�ȡֵΪ'progress'�����ع����¼����� |
| callback | (pg: DownloadProgress) =&gt; void | 是 | �ص����������ļ����ع����¼������Ϊ<br/>[DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md#DownloadProgress)������ֵΪvoid�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let download = new cloudSync.Download();

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});

```

## start

```TypeScript
start(uri: string): Promise<void>
```

�첽�����������ļ����ء�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

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
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.on('progress', (pg: cloudSync.DownloadProgress) => {
  console.info("download state: " + pg.state);
});

download.start(uri).then(() => {
  console.info("start download successfully");
}).catch((err: BusinessError) => {
  console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
});

```

## start

```TypeScript
start(uri: string, callback: AsyncCallback<void>): void
```

�첽�����������ļ����ء�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽�������ļ����ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.start(uri, (err: BusinessError) => {
  if (err) {
    console.error("start download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("start download successfully");
  }
});

```

## stop

```TypeScript
stop(uri: string): Promise<void>
```

�첽����ֹͣ���ļ����ء�ʹ��Promise�첽�ص���

> **˵����**
>
> ����stop�ӿڣ���ǰ�ļ��������̻���ֹ�������ļ��ᱻɾ�����ٴε���start�ӿڻ����¿�ʼ���ء�

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

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
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri).then(() => {
  console.info("stop download successfully");
}).catch((err: BusinessError) => {
  console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
});

```

## stop

```TypeScript
stop(uri: string, callback: AsyncCallback<void>): void
```

�첽����ֹͣ���ļ����ء�ʹ��callback�첽�ص���

> **˵����**
>
> ����stop�ӿڣ���ǰ�ļ��������̻���ֹ�������ļ��ᱻɾ�����ٴε���start�ӿڻ����¿�ʼ���ء�

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽ֹͣ���ļ����ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let download = new cloudSync.Download();
let uri: string = "file:///media/Photo/1";

download.stop(uri, (err: BusinessError) => {
  if (err) {
    console.error("stop download failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop download successfully");
  }
});

```

