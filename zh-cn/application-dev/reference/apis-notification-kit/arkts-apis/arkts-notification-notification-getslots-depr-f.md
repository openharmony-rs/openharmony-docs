# getSlots

## 导入模块

```TypeScript
```

## getSlots

```TypeScript
function getSlots(callback: AsyncCallback<Array<NotificationSlot>>): void
```

获取此应用程序的所有通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getSlots](arkts-notification-notificationmanager-getslots-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt;&gt; | 是 | 以callback形式返回获取此应用程序的所有通知通道的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

// getSlots回调
function getSlotsCallback(err: Base.BusinessError) {
  if (err) {
    console.error("getSlots failed " + JSON.stringify(err));
  } else {
    console.info("getSlots success");
  }
}
Notification.getSlots(getSlotsCallback);
```


## getSlots

```TypeScript
function getSlots(): Promise<Array<NotificationSlot>>
```

获取此应用程序的所有通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getSlots](arkts-notification-notificationmanager-getslots-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)&gt;&gt; | 以Promise形式返回获取此应用程序的所有通知通道的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.getSlots().then((data) => {
  console.info("getSlots success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getSlots failed, code is ${err}`);
});
```
