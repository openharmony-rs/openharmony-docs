# publish

## 导入模块

```TypeScript
```

## publish

```TypeScript
function publish(request: NotificationRequest, callback: AsyncCallback<void>): void
```

发布通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [publish](arkts-notification-notificationmanager-publish-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 发布通知的回调方法。 |

**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// publish回调
let publishCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error(`publish failed, code is ${err}`);
  } else {
    console.info("publish success");
  }
}
// 通知Request对象
let notificationRequest: NotificationManager.NotificationRequest = {
  id: 1,
  content: {
    contentType: Notification.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
Notification.publish(notificationRequest, publishCallback);
```


## publish

```TypeScript
function publish(request: NotificationRequest): Promise<void>
```

发布通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [publish](arkts-notification-notificationmanager-publish-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) | 是 | 用于设置要发布通知的内容和相关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// 通知Request对象
let notificationRequest: NotificationManager.NotificationRequest = {
  id: 1,
  content: {
    contentType: Notification.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
Notification.publish(notificationRequest).then(() => {
  console.info("publish success");
}).catch((err: Base.BusinessError) => {
  console.error(`publish failed, code is ${err}`);
});
```
