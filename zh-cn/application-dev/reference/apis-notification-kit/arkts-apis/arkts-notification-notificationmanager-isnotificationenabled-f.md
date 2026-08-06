# isNotificationEnabled

## isNotificationEnabled

```TypeScript
function isNotificationEnabled(callback: AsyncCallback<boolean>): void
```

查询当前应用通知授权状态。使用callback异步回调。 用于在发布通知前检查当前应用是否被允许发送通知，避免在通知授权关闭时发布导致失败。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本9 - 10：ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isNotificationEnabled(callback: AsyncCallback<boolean>): void--><!--Device-notificationManager-function isNotificationEnabled(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 是 | 回调函数。返回true，表示允许发布通知；返回false，表示禁止发布通知；调用失败返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 10 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 10 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isNotificationEnabledCallback = (err: BusinessError, data: boolean): void => {
  if (err) {
    console.error(`isNotificationEnabled failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isNotificationEnabled success, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.isNotificationEnabled(isNotificationEnabledCallback);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isNotificationEnabledCallback = (err: BusinessError | null, data: boolean | undefined | null): void => {
  if (err) {
    console.error(`isNotificationEnabled failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`isNotificationEnabled success, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.isNotificationEnabled(isNotificationEnabledCallback);
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(): Promise<boolean>
```

查询当前应用通知授权状态。使用Promise异步回调。 用于在发布通知前检查当前应用是否被允许发送通知，避免在通知使能关闭时发布导致失败。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本9 - 10：ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isNotificationEnabled(): Promise<boolean>--><!--Device-notificationManager-function isNotificationEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true，表示允许发布通知；返回false，表示禁止发布通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 10 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 9 - 10 |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 11+ |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isNotificationEnabled().then((data: boolean) => {
  console.info(`isNotificationEnabled success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isNotificationEnabled().then((data: boolean) => {
  console.info(`isNotificationEnabled success, data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`isNotificationEnabled failed, code is ${error.code}, message is ${error.message}`);
});
```

