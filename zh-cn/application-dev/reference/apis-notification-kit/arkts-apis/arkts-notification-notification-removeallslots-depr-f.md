# removeAllSlots

## 导入模块

```TypeScript
```

## removeAllSlots

```TypeScript
function removeAllSlots(callback: AsyncCallback<void>): void
```

删除所有通知通道（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let removeAllCallBack = (err: Base.BusinessError) => {
  if (err) {
    console.error("removeAllSlots failed " + JSON.stringify(err));
  } else {
    console.info("removeAllSlots success");
  }
}
Notification.removeAllSlots(removeAllCallBack);
```


## removeAllSlots

```TypeScript
function removeAllSlots(): Promise<void>
```

删除所有通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAllSlots](arkts-notification-notificationmanager-removeallslots-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.removeAllSlots().then(() => {
  console.info("removeAllSlots success");
}).catch((err: Base.BusinessError) => {
  console.error(`removeAllSlots failed, code is ${err}`);
});
```
