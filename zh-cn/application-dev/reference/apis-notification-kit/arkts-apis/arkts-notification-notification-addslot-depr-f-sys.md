# addSlot（系统接口）

## 导入模块

```TypeScript
```

## addSlot

```TypeScript
function addSlot(slot: NotificationSlot, callback: AsyncCallback<void>): void
```

创建通知渠道。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlot](arkts-notification-notificationmanager-addslot-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md) | 是 | 要创建的通知渠道对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定通道的回调方法。 |

**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// addslot回调
let addSlotCallBack = (err: Base.BusinessError) => {
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
Notification.addSlot(notificationSlot, addSlotCallBack);
```


## addSlot

```TypeScript
function addSlot(slot: NotificationSlot): Promise<void>
```

创建通知渠道。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlot](arkts-notification-notificationmanager-addslot-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md) | 是 | 要创建的通知渠道对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

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
