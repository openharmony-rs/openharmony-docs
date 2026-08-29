# addSlots（系统接口）

## 导入模块

```TypeScript
```

## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void
```

创建多个通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | 是 | 要创建的通知通道对象数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |

**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// addSlots回调
let addSlotsCallBack = (err: Base.BusinessError) => {
  if (err) {
    console.error("addSlots failed " + JSON.stringify(err));
  } else {
    console.info("addSlots success");
  }
}
// 通知slot对象
let notificationSlot: NotificationManager.NotificationSlot = {
  type: Notification.SlotType.SOCIAL_COMMUNICATION
};
// 通知slot array 对象
let notificationSlotArray: NotificationManager.NotificationSlot[] = new Array();
notificationSlotArray[0] = notificationSlot;

Notification.addSlots(notificationSlotArray, addSlotsCallBack);
```


## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>): Promise<void>
```

创建多个通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | 是 | 要创建的通知通道对象数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// 通知slot对象
let notificationSlot: NotificationManager.NotificationSlot = {
  type: Notification.SlotType.SOCIAL_COMMUNICATION
};
// 通知slot array 对象
let notificationSlotArray: NotificationManager.NotificationSlot[] = new Array();
notificationSlotArray[0] = notificationSlot;

Notification.addSlots(notificationSlotArray).then(() => {
  console.info("addSlots success");
}).catch((err: Base.BusinessError) => {
  console.error(`addSlot failed, code is ${err}`);
});
```
