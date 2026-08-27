# unmount（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## unmount

```TypeScript
function unmount(volumeId: string, callback: AsyncCallback<void>): void
```

卸载指定卷设备，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 卸载指定卷设备之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// volumeId可通过getAllVolumes()接口获取
let volumeId: string = "";
volumeManager.unmount(volumeId, (error: BusinessError) => {
  if (error) {
    console.error(`unmount failed, code is: ${error.code}, message is: ${error.message}`);
    return;
  }
  // 卸载指定卷设备成功后的回调
});
```


## unmount

```TypeScript
function unmount(volumeId: string): Promise<void>
```

卸载指定卷设备，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// volumeId可通过getAllVolumes()接口获取
let volumeId: string = "";
volumeManager.unmount(volumeId).then(() => {
  // 卸载指定卷设备成功后的回调
}).catch((error: BusinessError) => {
  console.error(`Failed to unmount. Code: ${error.code}, message: ${error.message}`);
});
```
