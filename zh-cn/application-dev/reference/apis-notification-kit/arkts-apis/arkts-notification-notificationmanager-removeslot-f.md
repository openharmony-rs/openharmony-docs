# removeSlot

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## removeSlot

```TypeScript
function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void
```

删除当前应用指定类型的通知渠道。使用callback异步回调。

删除后，对应类型的通知渠道及其配置将被永久移除，后续发布该类型通知时系统将自动创建默认渠道。已通过该渠道发布的通知不受影响，仍可在通知中心查看。适用于需要重新配置渠道时先删除再创建的场景。

**起始版本：** 9

<!--Device-notificationManager-function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function removeSlot(slotType: SlotType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。需传入已创建的渠道类型，否则删除操作无效。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当删除指定类型的通知渠道成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// removeSlot回调
let removeSlotCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to remove slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in removing slot.`);
  }
}
let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.removeSlot(slotType, removeSlotCallback);

```


## removeSlot

```TypeScript
function removeSlot(slotType: SlotType): Promise<void>
```

删除当前应用指定类型的通知渠道。使用Promise异步回调。

删除后，对应类型的通知渠道及其配置将被永久移除，后续发布该类型通知时系统将自动创建默认渠道。已通过该渠道发布的通知不受影响，仍可在通知中心查看。适用于需要重新配置渠道时先删除再创建的场景。

**起始版本：** 9

<!--Device-notificationManager-function removeSlot(slotType: SlotType): Promise<void>--><!--Device-notificationManager-function removeSlot(slotType: SlotType): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | [SlotType](arkts-notification-notificationmanager-slottype-e.md) | 是 | 通知渠道类型，例如社交通讯、服务提醒、内容咨询等类型。需传入已创建的渠道类型，否则删除操作无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.removeSlot(slotType).then(() => {
  console.info(`Succeeded in removing slot.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to remove slot. Code is ${err.code}, message is ${err.message}`);
});

```

