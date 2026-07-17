# partition（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## partition

```TypeScript
function partition(diskId: string, type: number, callback: AsyncCallback<void>): void
```

对磁盘进行分区，使用callback异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。不支持对光盘进行分区。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_FORMAT_MANAGER

<!--Device-volumeManager-function partition(diskId: string, type: int, callback: AsyncCallback<void>): void--><!--Device-volumeManager-function partition(diskId: string, type: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| diskId | string | 是 | 卷设备所属的磁盘id。 |
| type | number | 是 | 分区类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 对磁盘设备进行分区。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |


## partition

```TypeScript
function partition(diskId: string, type: number): Promise<void>
```

对磁盘设备进行分区，使用Promise异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。不支持对光盘进行分区。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_FORMAT_MANAGER

<!--Device-volumeManager-function partition(diskId: string, type: int): Promise<void>--><!--Device-volumeManager-function partition(diskId: string, type: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| diskId | string | 是 | 卷设备所属的磁盘设备id。 |
| type | number | 是 | 分区类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

