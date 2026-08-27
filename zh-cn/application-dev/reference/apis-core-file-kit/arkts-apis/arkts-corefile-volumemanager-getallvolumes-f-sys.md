# getAllVolumes（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getAllVolumes

```TypeScript
function getAllVolumes(callback: AsyncCallback<Array<Volume>>): void
```

获取当前外置存储中所有卷设备信息，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Volume](arkts-corefile-volumemanager-volume-i-sys.md)&gt;&gt; | 是 | 获取当前所有可获得的卷设备信息之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
volumeManager.getAllVolumes((error: BusinessError, volumes: Array<volumeManager.Volume>) => {
  if (error) {
    console.error(`getAllVolumes failed, code is: ${error.code}, message is: ${error.message}`);
    return;
  }
  // 获取到所有卷设备信息
});
```


## getAllVolumes

```TypeScript
function getAllVolumes(): Promise<Array<Volume>>
```

获取当前外置存储中所有卷设备信息，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[Volume](arkts-corefile-volumemanager-volume-i-sys.md)&gt;&gt; | Promise对象，返回当前所有可获得的卷设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The input parameter is invalid.Possible causes:Mandatory parameters are left unspecified; |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
  // 获取到所有卷设备信息
}).catch((error: BusinessError) => {
  console.error(`Failed to getAllVolumes. Code: ${error.code}, message: ${error.message}`);
});
```
