# getFreeSizeOfVolume（系统接口）

## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<long>): void
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以callback方式返回。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<long>): void--><!--Device-storageStatistics-function getFreeSizeOfVolume(volumeUuid: string, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeUuid | string | 是 | 卷设备uuid。 |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;long&gt; | 是 | 获取指定卷可用空间之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid, (error: BusinessError, freeSize: number) => {
    if (error) {
      console.error(`getFreeSizeOfVolume failed with err, code is: ${error.code}, message is: ${error.message}`);
    } else {
      // do something
      console.info("getFreeSizeOfVolume successfully: " + freeSize);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid, (error: BusinessError, freeSize: long): void => {
    if (error) {
      console.error(`getFreeSizeOfVolume failed with err, code is: ${error.code}, message is: ${error.message}`);
    } else {
      // do something
      console.info("getFreeSizeOfVolume successfully: " + freeSize);
    }
  });
}).catch((err: BusinessError): void => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```


## getFreeSizeOfVolume

```TypeScript
function getFreeSizeOfVolume(volumeUuid: string): Promise<long>
```

异步获取外置存储设备中指定卷设备的可用空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

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
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回指定卷的可用空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid).then((freeSize: number) => {
    console.info("getFreeSizeOfVolume successfully:" + number);
  }).catch((err: BusinessError) => {
    console.error(`getFreeSizeOfVolume failed with err, code is: ${err.code}, message is: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  let uuid: string = volumes[0].uuid;
  storageStatistics.getFreeSizeOfVolume(uuid).then((freeSize: long) => {
    console.info("getFreeSizeOfVolume successfully:" + freeSize);
  }).catch((err: BusinessError): void => {
    console.error(`getFreeSizeOfVolume failed with err, code is: ${err.code}, message is: ${err.message}`);
  });
}).catch((err: BusinessError): void => {
  console.error(`getAllVolumes failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

