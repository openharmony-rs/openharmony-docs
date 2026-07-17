# enableCloud（系统接口）

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## enableCloud

```TypeScript
function enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>
```

异步方法使能端云协同能力。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>--><!--Device-cloudSyncManager-function enableCloud(accountId: string, switches: Record<string, boolean>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| switches | Record<string, boolean> | 是 | 应用的端云协同特性使能开关，string类型为应用包名，boolean类型为开关状态。true为打开；false为关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches).then(() => {
  console.info("enableCloud successfully.");
}).catch((err: BusinessError) => {
  console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});

```


## enableCloud

```TypeScript
function enableCloud(
    accountId: string,
    switches: Record<string, boolean>,
    callback: AsyncCallback<void>
  ): void
```

异步方法使能端云协同能力。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function enableCloud(
    accountId: string,
    switches: Record<string, boolean>,
    callback: AsyncCallback<void>
  ): void--><!--Device-cloudSyncManager-function enableCloud(
    accountId: string,
    switches: Record<string, boolean>,
    callback: AsyncCallback<void>
  ): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| switches | Record<string, boolean> | 是 | 应用的端云协同特性使能开关，string类型为应用包名，boolean类型为开关状态。true为打开；false为关闭。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。异步使能端云协同能力之后。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches, (err: BusinessError) => {
  if (err) {
    console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("enableCloud successfully");
  }
});

```

