# getActiveNotificationCount

## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(callback: AsyncCallback<long>): void
```

获取当前应用的通知数量。使用callback异步回调。 用于查询当前应用在通知中心中已发布的存量通知数量。适用于需要展示未读通知数量提示的场景。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-notificationManager-function getActiveNotificationCount(callback: AsyncCallback<long>): void--><!--Device-notificationManager-function getActiveNotificationCount(callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;long&gt; | 是 | 回调函数。当获取当前应用未删除的通知数成功，err为undefined，data为当前应用未删除的通知数，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationCountCallback = (err: BusinessError, data: number): void => {
  if (err) {
    console.error(`Failed to get active notification count. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.getActiveNotificationCount(getActiveNotificationCountCallback);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let getActiveNotificationCountCallback = (err: BusinessError | null, data: long | undefined | null): void => {
  if (err) {
    console.error(`Failed to get active notification count. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
  }
}

notificationManager.getActiveNotificationCount(getActiveNotificationCountCallback);
```


## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(): Promise<long>
```

获取当前应用的通知数量。使用Promise异步回调。 用于查询当前应用在通知中心中已发布的存量通知数量。适用于需要展示未读通知数量提示的场景。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-notificationManager-function getActiveNotificationCount(): Promise<long>--><!--Device-notificationManager-function getActiveNotificationCount(): Promise<long>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回当前应用未删除通知数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotificationCount().then((data: number) => {
  console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get active notification count. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getActiveNotificationCount().then((data: long) => {
  console.info(`Succeeded in getting active notification count, data is ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get active notification count. Code is ${error.code}, message is ${error.message}`);
});
```

