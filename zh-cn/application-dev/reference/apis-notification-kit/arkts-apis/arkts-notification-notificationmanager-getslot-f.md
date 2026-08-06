# getSlot

## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void
```

获取指定类型的通知渠道。使用callback异步回调。 用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。 需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-notificationManager-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void--><!--Device-notificationManager-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NotificationSlot&gt; | 是 | 回调函数。当获取通知渠道成功，err为undefined，data为获取到的NotificationSlot，否则为错误对象。 |

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

// getSlot回调
let getSlotCallback = (err: BusinessError, data: notificationManager.NotificationSlot): void => {
  if (err) {
    console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
  }
}
let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType, getSlotCallback);
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// getSlot回调
let getSlotCallback = (err: BusinessError<void> | null, data: notificationManager.NotificationSlot | undefined | null) : void => {
  if (err) {
    console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
  } else if (data) {
    console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
  } else {
    console.warn('getSlot returned no error but also no data');
  }
};

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION
notificationManager.getSlot(slotType, getSlotCallback);
```


## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot|null>): void
```

获取指定类型的通知渠道。使用callback异步回调。 用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。 需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-notificationManager-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot|null>): void--><!--Device-notificationManager-function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot|null>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NotificationSlot \| null&gt; | 是 | 回调函数。当获取通知渠道成功，err为undefined，data为获取到的NotificationSlot，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |


## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot>
```

获取指定类型的通知渠道。使用Promise异步回调。 用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。 需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-notificationManager-function getSlot(slotType: SlotType): Promise<NotificationSlot>--><!--Device-notificationManager-function getSlot(slotType: SlotType): Promise<NotificationSlot>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSlot&gt; | Promise对象，返回通知渠道对象。 |

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

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType).then((data: notificationManager.NotificationSlot) => {
  console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType).then((data: notificationManager.NotificationSlot | null) => {
    console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
  }).catch((err: Error): void => {
    let error: BusinessError = err as BusinessError;
    console.error(`Failed to get slot. Code is ${error.code}, message is ${error.message}`);
  });
```


## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot|null>
```

获取指定类型的通知渠道。使用Promise异步回调。 用于查询已创建的通知渠道的详细配置信息，包括提醒方式、级别、锁屏显示等设置。 需先通过addSlot创建对应类型的通知渠道，否则获取结果为空。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-notificationManager-function getSlot(slotType: SlotType): Promise<NotificationSlot|null>--><!--Device-notificationManager-function getSlot(slotType: SlotType): Promise<NotificationSlot|null>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSlot \| null&gt; | Promise对象，返回通知渠道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

