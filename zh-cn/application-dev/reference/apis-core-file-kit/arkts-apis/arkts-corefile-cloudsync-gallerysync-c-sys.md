# GallerySync（系统接口）

��ͼͬ����������֧��ͼ��Ӧ��ý����Դ����ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���GallerySyncʵ����

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

����ͬ�����̵Ĺ��캯�������ڻ�ȡGallerySync���ʵ����

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync()

```

## off

```TypeScript
off(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

��ͼͬ�������Ƴ�'progress'������ָ����callback�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | (pg: SyncProgress) =&gt; void | 是 | �ص�������ͬ�������¼������Ϊ[SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md#SyncProgress)����<br/>��ֵΪvoid�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

let callback = (pg: cloudSync.SyncProgress) => {
  console.info("gallery sync state: " + pg.state + "error type: " + pg.error);
}

gallerySync.on('progress', callback);

gallerySync.off('progress', callback);

```

## off

```TypeScript
off(evt: 'progress'): void
```

��ͼͬ�������Ƴ�'progress'���͵����лص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ȡ�����ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
    console.info("syncState: " + pg.state);
});

gallerySync.off('progress');

```

## on

```TypeScript
on(evt: 'progress', callback: (pg: SyncProgress) => void): void
```

��ͼͬ����������ͬ�������¼�������

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| evt | 'progress' | 是 | ���ĵ��¼����ͣ�ȡֵΪ'progress'��ͬ�������¼����� |
| callback | (pg: SyncProgress) =&gt; void | 是 | �ص�������ͬ�������¼������Ϊ[SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md#SyncProgress)����<br/>��ֵΪvoid�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error |

**示例：**

```TypeScript
let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});

```

## start

```TypeScript
start(): Promise<void>
```

��������ͬ����ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |
| [22400001](../../errorcode-universal.md#22400001-Cloud) | Cloud status not ready. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400003](../../errorcode-universal.md#22400003-Low) | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.on('progress', (pg: cloudSync.SyncProgress) => {
  console.info("syncState: " + pg.state);
});

gallerySync.start().then(() => {
  console.info("start sync successfully");
}).catch((err: BusinessError) => {
  console.error("start sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

�첽������������ͬ����ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽��������ͬ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [22400001](../../errorcode-universal.md#22400001-Cloud) | Cloud status not ready. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400003](../../errorcode-universal.md#22400003-Low) | Low battery level. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.start((err: BusinessError) => {
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

�첽����ֹͣ����ͬ����ʹ��Promise�첽�ص���

> **˵����**
>
> ����stop�ӿڣ�ͬ�����̻�ֹͣ���ٴε���[start](arkts-corefile-cloudsync-gallerysync-c-sys.md#start-1)�ӿڻ����ͬ����

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop().then(() => {
  console.info("stop sync successfully");
}).catch((err: BusinessError) => {
  console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

�첽����ֹͣ����ͬ����ʹ��callback�첽�ص���

> **˵����**
>
> ����stop�ӿڣ�ͬ�����̻�ֹͣ���ٴε���[start](arkts-corefile-cloudsync-gallerysync-c-sys.md#start-1)�ӿڻ����ͬ����

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������첽ֹͣ����ͬ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let gallerySync = new cloudSync.GallerySync();

gallerySync.stop((err: BusinessError) => {
  if (err) {
    console.error("stop sync failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("stop sync successfully");
  }
});

```

