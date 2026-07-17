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

<!--Device-volumeManager-function getVolumeByUuid(uuid: string, callback: AsyncCallback<Volume>): void--><!--Device-volumeManager-function getVolumeByUuid(uuid: string, callback: AsyncCallback<Volume>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Volume> | 是 | 获取卷设备信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |


## getVolumeByUuid

```TypeScript
function getVolumeByUuid(uuid: string): Promise<Volume>
```

通过卷设备uuid获得指定卷设备信息，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

<!--Device-volumeManager-function getVolumeByUuid(uuid: string): Promise<Volume>--><!--Device-volumeManager-function getVolumeByUuid(uuid: string): Promise<Volume>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Volume> | Promise对象，返回当前uuid的卷设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

