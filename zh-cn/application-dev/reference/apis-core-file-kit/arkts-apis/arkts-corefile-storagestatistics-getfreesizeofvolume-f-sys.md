# getFreeSizeOfVolume（系统接口）

## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<number>): void
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。

**起始版本：** 8

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeUuid | string | 是 | 卷设备uuid。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 获取指定卷可用空间之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory<br/>parameters are left unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13600008](../../errorcode-universal.md#13600008-No) | No such object. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

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
      console.error("getFreeSizeOfVolume failed with error:" + JSON.stringify(error));
    } else {
      // do something
      console.info("getFreeSizeOfVolume successfully: " + number);
    }
  });
}).catch((err: BusinessError) => {
  console.error("getAllVolumes failed with error:" + JSON.stringify(err));
});

```


## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string): Promise<number>
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 8

**需要权限：** ohos.permission.STORAGE_MANAGER

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
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-The) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory<br/>parameters are left unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13600008](../../errorcode-universal.md#13600008-No) | No such object. |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error. |

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
    console.error("getFreeSizeOfVolume failed with error:" + JSON.stringify(err));
  });
}).catch((err: BusinessError) => {
  console.error("getAllVolumes failed with error:" + JSON.stringify(err));
});

```

