# clean（系统接口）

## clean

```TypeScript
function clean(accountId: string, appActions: Record<string, Action>): Promise<void>
```

异步方法清理本地云相关数据。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function clean(accountId: string, appActions: Record<string, Action>): Promise<void>--><!--Device-cloudSyncManager-function clean(accountId: string, appActions: Record<string, Action>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| appActions | Record&lt;string, Action&gt; | 是 | 清理动作类型，string类型为待清理应用包名， [Action]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_为清理动作类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions).then(() => {
  console.info("clean successfully");
}).catch((err: BusinessError) => {
  console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = new Record<string, cloudSyncManager.Action>();
appActions['com.example.bundleName1'] = cloudSyncManager.Action.RETAIN_DATA;
appActions['com.example.bundleName2'] = cloudSyncManager.Action.CLEAR_DATA;
cloudSyncManager.clean(accountId, appActions).then<void>((): void => {
  console.info("clean successfully");
}).catch((err: BusinessError<void>): void => {
  console.error("clean failed with error message: " + err.message + ", error code: " + err.code);
});
```


## clean

```TypeScript
function clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback<void>): void
```

异步方法清理本地云相关数据。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-cloudSyncManager-function clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback<void>): void--><!--Device-cloudSyncManager-function clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | string | 是 | 账号Id。 |
| appActions | Record&lt;string, Action&gt; | 是 | 清理动作类型，string类型为待清理应用包名， [Action]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_为清理动作类型。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。异步方法清理本地云相关数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions, (err: BusinessError) => {
  if (err) {
    console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("clean successfully");
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = new Record<string, cloudSyncManager.Action>();
appActions['com.example.bundleName1'] = cloudSyncManager.Action.RETAIN_DATA;
appActions['com.example.bundleName2'] = cloudSyncManager.Action.CLEAR_DATA;
cloudSyncManager.clean(accountId, appActions, (err: BusinessError<void> | null): void => {
  if (err && err.code) {
    console.error("clean failed with error message: " + err.message + ", error code: " + err.code);
  } else {
    console.info("clean successfully");
  }
});
```

