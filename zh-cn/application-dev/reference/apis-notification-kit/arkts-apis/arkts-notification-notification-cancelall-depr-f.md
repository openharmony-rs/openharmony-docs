# cancelAll

## 导入模块

```TypeScript
```

## cancelAll

```TypeScript
function cancelAll(callback: AsyncCallback<void>): void
```

取消所有已发布的通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [cancelAll](arkts-notification-notificationmanager-cancelall-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |

**示例**

```TypeScript
import Base from '@ohos.base';

// cancel回调
let cancelAllCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("cancelAll failed " + JSON.stringify(err));
  } else {
    console.info("cancelAll success");
  }
}
Notification.cancelAll(cancelAllCallback);
```


## cancelAll

```TypeScript
function cancelAll(): Promise<void>
```

取消所有已发布的通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [cancelAll](arkts-notification-notificationmanager-cancelall-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.cancelAll().then(() => {
  console.info("cancelAll success");
}).catch((err: Base.BusinessError) => {
  console.error(`cancelAll failed, code is ${err}`);
});
```
