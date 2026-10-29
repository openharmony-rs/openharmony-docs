# addSlot（系统接口）

## 导入模块

```TypeScript
```

## addSlot

```TypeScript
function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

创建通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-1)(slot: NotificationSlot, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-i.md) | 是 | 要创建的通知通道对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |

<!--Del-->
**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// addslot回调
let addSlotCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("addSlot failed " + JSON.stringify(err));
  } else {
    console.info("addSlot success");
  }
}
// 通知slot对象
let notificationSlot: NotificationManager.NotificationSlot = {
  type: Notification.SlotType.SOCIAL_COMMUNICATION
};
Notification.addSlot(notificationSlot, addSlotCallback);
```

<!--DelEnd-->


## addSlot

```TypeScript
function addSlot(slot: NotificationSlot): Promise<void>
```

创建通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlot](arkts-notification-notificationmanager-addslot-f-sys.md#addslot-2)(slot: NotificationSlot)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>--><!--Device-notification-function addSlot(slot: NotificationSlot): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-i.md) | 是 | 要创建的通知通道对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

<!--Del-->
**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// 通知slot对象
let notificationSlot: NotificationManager.NotificationSlot = {
    type: Notification.SlotType.SOCIAL_COMMUNICATION
};
Notification.addSlot(notificationSlot).then(() => {
  console.info("addSlot success");
}).catch((err: Base.BusinessError) => {
  console.error(`addSlot failed, code is ${err}`);
});
```

<!--DelEnd-->
