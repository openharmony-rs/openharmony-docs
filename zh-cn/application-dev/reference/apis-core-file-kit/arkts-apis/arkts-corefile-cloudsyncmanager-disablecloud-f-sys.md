# disableCloud（系统接口）

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## disableCloud

```TypeScript
function disableCloud(accountId: string): Promise<void>
```

异步方法去使能端云协同能力。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function disableCloud(accountId: string): Promise<void>--><!--Device-cloudSyncManager-function disableCloud(accountId: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |

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
cloudSyncManager.disableCloud(accountId).then(() => {
  console.info("disableCloud successfully");
}).catch((err: BusinessError) => {
  console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});

```


## disableCloud

```TypeScript
function disableCloud(accountId: string, callback: AsyncCallback<void>): void
```

异步方法去使能端云协同能力。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function disableCloud(accountId: string, callback: AsyncCallback<void>): void--><!--Device-cloudSyncManager-function disableCloud(accountId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。异步去使能端云协同能力之后。 |

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
cloudSyncManager.disableCloud(accountId, (err: BusinessError) => {
  if (err) {
    console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("disableCloud successfully");
  }
});

```

