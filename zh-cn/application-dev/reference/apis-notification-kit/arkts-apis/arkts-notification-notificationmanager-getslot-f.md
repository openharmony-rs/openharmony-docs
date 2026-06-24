# getSlot

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## getSlot

```TypeScript
function getSlot(slotType: SlotType, callback: AsyncCallback<NotificationSlot>): void
```

获取指定类型的通知渠道。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | SlotType | 是 | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |
| callback | AsyncCallback&lt;NotificationSlot&gt; | 是 | 回调函数。当获取通知渠道成功，err为undefined，data为获取到的NotificationSlot，否则为错误对<br/>象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

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


## getSlot

```TypeScript
function getSlot(slotType: SlotType): Promise<NotificationSlot>
```

获取指定类型的通知渠道。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotType | SlotType | 是 | 通知渠道类型，例如社交通信、服务提醒、内容咨询等类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSlot&gt; | Promise对象，返回通知渠道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotType: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
notificationManager.getSlot(slotType).then((data: notificationManager.NotificationSlot) => {
  console.info(`Succeeded in getting slot, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get slot. Code is ${err.code}, message is ${err.message}`);
});

```

