# getFreeSizeOfVolume（系统接口）

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

<a id="getfreesizeofvolume"></a>
## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<number>): void
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。

**起始版本：** 8

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeUuid | string | 是 | 卷设备uuid。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 获取指定卷可用空间之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  if (volumes == null || volumes.length <= 0) {
    console.error("volumes is null or length is invalid");
    return;
  }
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid, (error: BusinessError, number: number) => {
    if (error) {
      console.error(`getFreeSizeOfVolume failed with err, code is: ${error.code}, message is: ${error.message}`);
    } else {
      // do something
      console.info("getFreeSizeOfVolume successfully: " + number);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});

```


<a id="getfreesizeofvolume-1"></a>
## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string): Promise<number>
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 8

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string): Promise<long>--><!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeUuid | string | 是 | 卷设备uuid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回指定卷的可用空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  if (volumes == null || volumes.length <= 0) {
    console.error("volumes is null or length is invalid");
    return;
  }
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid).then((number: number) => {
    console.info("getFreeSizeOfVolume successfully:" + number);
  }).catch((err: BusinessError) => {
    console.error(`getFreeSizeOfVolume failed with err, code is: ${err.code}, message is: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});

```

