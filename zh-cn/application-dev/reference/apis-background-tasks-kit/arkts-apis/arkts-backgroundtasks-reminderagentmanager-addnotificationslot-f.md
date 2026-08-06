# addNotificationSlot

## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

添加通知渠道。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-reminderAgentManager-function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-reminderAgentManager-function addNotificationSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道实例，仅支持设置其notificationType属性。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当添加NotificationSlot成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}

reminderAgentManager.addNotificationSlot(mySlot, (err: BusinessError) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("addNotificationSlot callback");
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let addCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in adding slot.`);
  }
}

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}

reminderAgentManager.addNotificationSlot(mySlot, addCallback);
```


## addNotificationSlot

```TypeScript
function addNotificationSlot(slot: NotificationSlot): Promise<void>
```

添加通知渠道。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-reminderAgentManager-function addNotificationSlot(slot: NotificationSlot): Promise<void>--><!--Device-reminderAgentManager-function addNotificationSlot(slot: NotificationSlot): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知渠道实例，仅支持设置其notificationType属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}
reminderAgentManager.addNotificationSlot(mySlot).then(() => {
  console.info("addNotificationSlot promise");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let mySlot: notificationManager.NotificationSlot = {
  notificationType: notificationManager.SlotType.SOCIAL_COMMUNICATION
}
reminderAgentManager.addNotificationSlot(mySlot).then(() => {
  console.info(`Succeeded in adding slot.`);
}).catch((err): void => {
  console.error(`Failed to add slot. Code is ${err.code}, message is ${err.message}`);
});
```

