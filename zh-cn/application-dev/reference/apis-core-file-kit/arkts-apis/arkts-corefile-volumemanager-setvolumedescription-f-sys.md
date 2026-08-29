# setVolumeDescription（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## setVolumeDescription

```TypeScript
function setVolumeDescription(uuid: string, description: string, callback: AsyncCallback<void>): void
```

修改指定卷设备描述，使用callback异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述， 只有处于卸载状态的卷设备可以修改设备描述。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| description | string | 是 | 卷设备描述。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设置卷描述之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// uuid可通过getAllVolumes()接口获取卷设备信息后获得
let uuid: string = "";
let description: string = "";
volumeManager.setVolumeDescription(uuid, description, (error: BusinessError) => {
  if (error) {
    console.error(`setVolumeDescription failed, code is: ${error.code}, message is: ${error.message}`);
    return;
  }
  // 设置卷设备描述成功的回调
});
```


## setVolumeDescription

```TypeScript
function setVolumeDescription(uuid: string, description: string): Promise<void>
```

修改指定卷设备描述，使用Promise异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述， 只有处于卸载状态的卷设备可以修改设备描述。

**起始版本：** 9

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 卷设备uuid。 |
| description | string | 是 | 卷设备描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes: 1.Mandatory parameters are left unspecified;  2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// uuid可通过getAllVolumes()接口获取卷设备信息后获得
let uuid: string = "";
let description: string = "";
volumeManager.setVolumeDescription(uuid, description).then(() => {
  console.info("setVolumeDescription successfully");
}).catch((error: BusinessError) => {
  console.error(`Failed to setVolumeDescription. Code: ${error.code}, message: ${error.message}`);
});
```
