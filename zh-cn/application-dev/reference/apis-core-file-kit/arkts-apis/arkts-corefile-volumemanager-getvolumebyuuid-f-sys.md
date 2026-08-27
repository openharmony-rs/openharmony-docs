# getVolumeByUuid（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getVolumeByUuid

```TypeScript
function getVolumeByUuid(uuid: string, callback: AsyncCallback<Volume>): void
```

通过卷设备uuid获得指定卷设备信息，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Volume](arkts-corefile-volumemanager-volume-i-sys.md)&gt; | 是 | 获取卷设备信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// uuid可通过getAllVolumes()接口获取卷设备信息后获得
let uuid: string = "";
volumeManager.getVolumeByUuid(uuid, (error: BusinessError, volume: volumeManager.Volume) => {
  if (error) {
    console.error(`getVolumeByUuid failed, code is: ${error.code}, message is: ${error.message}`);
    return;
  }
  // 获取到卷设备信息
});
```


## getVolumeByUuid

```TypeScript
function getVolumeByUuid(uuid: string): Promise<Volume>
```

通过卷设备uuid获得指定卷设备信息，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Volume](arkts-corefile-volumemanager-volume-i-sys.md)&gt; | Promise对象，返回当前uuid的卷设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// uuid可通过getAllVolumes()接口获取卷设备信息后获得
let uuid: string = "";
volumeManager.getVolumeByUuid(uuid).then((volume: volumeManager.Volume) => {
  console.info("getVolumeByUuid successfully:" + JSON.stringify(volume));
}).catch((error: BusinessError) => {
  console.error(`Failed to getVolumeByUuid. Code: ${error.code}, message: ${error.message}`);
});
```
