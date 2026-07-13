# SyncFolderAccessor（系统接口）

同步根管理类，负责为系统文件管理应用提供获取三方网盘注册的同步根信息的能力。

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

SyncFolderAccessor的构造函数，用于获取SyncFolderAccessor类的实例。

**起始版本：** 21

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed.application which is not a system application uses system API. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('constructor')
      .onClick(async() => {
          try {
            let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
          } catch (err) {
              let error: BusinessError = err as BusinessError;
              console.error(`SyncFolderAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
          }
      });
    }
  }
}


```

## getAllSyncFolders

```TypeScript
getAllSyncFolders(): Promise<Array<SyncFolder>>
```

获取所有注册的同步根信息。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;SyncFolder&gt;&gt; | Promise对象。返回所有网盘应用的同步根列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Device not supported. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc通信失败) | IPC communication failed. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure. Retry is recommended (e.g., network issues). |
| [34400015](../errorcode-clouddiskmanager-sys.md#34400015-当前设备不允许使用云盘功能) | Cloud disk is not allowed on this device. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
const TAG: string = '[cloudDiskManager]';

try {
    console.info(TAG + `getAllSyncFolders start`);
    let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
    syncFolderAccessor.getAllSyncFolders().then((syncFolders) => {
        if (syncFolders) {
            console.info(TAG + `getAllSyncFolders success, length: ${syncFolders.length}`);
            for (let i = 0; i < syncFolders.length; ++i) {
                console.info(TAG + `syncFolders[${i}].path: ${syncFolders[i].path}`);
                console.info(TAG + `syncFolders[${i}].bundleName: ${syncFolders[i].bundleName}`);
                console.info(TAG + `syncFolders[${i}].state: ${syncFolders[i].state}`);
                if (syncFolders[i].displayNameResId) {
                    console.info(TAG + `syncFolders[${i}].displayNameResId: ${syncFolders[i].displayNameResId}`);
                }
                if (syncFolders[i].customAlias) {
                    console.info(TAG + `syncFolders[${i}].customAlias: ${syncFolders[i].customAlias}`);
                }
            }
        } else {
            console.info(TAG + `getAllSyncFolders failed`);
        }
    }).catch((e: BusinessError<object>) => {
        console.error(TAG + `getAllSyncFolders then catch err, code: ${e.code}, message: ${e.message}`);
    })
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(TAG + `getAllSyncFolders failed. code: ${error.code}, message: ${error.message}`);
}

```

