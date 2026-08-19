# removeAllSlots

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
import { notificationSubscribe } from '@kit.NotificationKit';
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## removeAllSlots

```TypeScript
function removeAllSlots(callback: AsyncCallback<void>): void
```

删除所有通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md)

<!--Device-notification-function removeAllSlots(callback: AsyncCallback<void>): void--><!--Device-notification-function removeAllSlots(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


## removeAllSlots

```TypeScript
function removeAllSlots(): Promise<void>
```

删除所有通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md)

<!--Device-notification-function removeAllSlots(): Promise<void>--><!--Device-notification-function removeAllSlots(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

