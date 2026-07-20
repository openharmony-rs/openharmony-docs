# setBadgeNumber

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="setbadgenumber"></a>
## setBadgeNumber

```TypeScript
function setBadgeNumber(badgeNumber: number, callback: AsyncCallback<void>): void
```

设定角标个数，在应用的桌面图标上呈现。使用callback异步回调。

角标是应用桌面图标右上角显示的数字标识，用于提示用户有未处理的通知数量。设定后，桌面图标将显示对应角标数字。适用于需要在桌面图标上提示用户待处理消息数量的场景，如未读消息数、待办事项数等。

**起始版本：** 10

<!--Device-notificationManager-function setBadgeNumber(badgeNumber: int, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function setBadgeNumber(badgeNumber: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| badgeNumber | number | 是 | 角标个数。当角标设定个数取值小于或等于0时，清除角标。取值大于99时，通知角标将显示99+。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设定角标个数成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let setBadgeNumberCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in setting badge number.`);
  }
}
let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber, setBadgeNumberCallback);

```


<a id="setbadgenumber-1"></a>
## setBadgeNumber

```TypeScript
function setBadgeNumber(badgeNumber: number): Promise<void>
```

设定角标个数，在应用的桌面图标上呈现。使用Promise异步回调。

角标是应用桌面图标右上角显示的数字标识，用于提示用户有未处理的通知数量。设定后，桌面图标将显示对应角标数字。适用于需要在桌面图标上提示用户待处理消息数量的场景，如未读消息数、待办事项数等。

**起始版本：** 10

<!--Device-notificationManager-function setBadgeNumber(badgeNumber: int): Promise<void>--><!--Device-notificationManager-function setBadgeNumber(badgeNumber: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| badgeNumber | number | 是 | 角标个数。当角标设定个数取值小于或等于0时，清除角标。取值大于99时，通知角标将显示99+。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let badgeNumber: number = 10;
notificationManager.setBadgeNumber(badgeNumber).then(() => {
  console.info(`Succeeded in setting badge number.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set badge number. Code is ${err.code}, message is ${err.message}`);
});

```

