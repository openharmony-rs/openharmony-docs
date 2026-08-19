# addSlots（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { notificationSubscribe } from '@kit.NotificationKit';
import { notificationExtensionSubscription } from '@kit.NotificationKit';
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

<!--Device-notification-function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void--><!--Device-notification-function addSlots(slots: Array<NotificationSlot>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | 是 | 要创建的通知通道对象数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


## addSlots

```TypeScript
function addSlots(slots: Array<NotificationSlot>): Promise<void>
```

创建多个通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addSlots](arkts-notification-notificationmanager-addslots-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function addSlots(slots: Array<NotificationSlot>): Promise<void>--><!--Device-notification-function addSlots(slots: Array<NotificationSlot>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slots | Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt; | 是 | 要创建的通知通道对象数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

