# notifyDataChange（系统接口）

## notifyDataChange

```TypeScript
function notifyDataChange(accountId: string, bundleName: string): Promise<void>
```

通知端云服务指定账号下的特定应用云数据已发生变更。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});

```


## notifyDataChange

```TypeScript
function notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback<void>): void
```

通知端云服务指定账号下的特定应用云数据已发生变更。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| bundleName | string | 是 | 应用包名。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。异步通知端云服务应用的云数据变更之后的。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});

```


## notifyDataChange

```TypeScript
function notifyDataChange(userId: number, extraData: ExtraData): Promise<void>
```

通知端云服务应用指定用户的云数据变更信息。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户Id。 |
| extraData | ExtraData | 是 | 云端数据变更信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application usessystem API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});

```


## notifyDataChange

```TypeScript
function notifyDataChange(userId: number, extraData: ExtraData, callback: AsyncCallback<void>): void
```

通知端云服务应用指定用户的云数据变更信息。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户Id。 |
| extraData | ExtraData | 是 | 云端数据变更信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。异步通知端云服务应用的云数据变更之后。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application usessystem API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});

```

