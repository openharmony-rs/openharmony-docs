# publish（系统接口）

## 导入模块

```TypeScript
```

## publish

```TypeScript
function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void
```

发布通知给指定的用户（callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [publish](arkts-notification-notificationmanager-publish-f.md)(request: NotificationRequest, userId: number, callback: AsyncCallback&lt;void&gt;)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void--><!--Device-notification-function publish(request: NotificationRequest, userId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationrequest-i.md) | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| userId | number | 是 | 用户ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 被指定的回调方法。 |

<!--Del-->
**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

// publish回调
let publishCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error(`publish failed, code is ${err.code}`);
  } else {
    console.info("publish success");
  }
}
// 用户ID
let userId: number = 1;
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
Notification.publish(notificationRequest, userId, publishCallback);
```

<!--DelEnd-->


## publish

```TypeScript
function publish(request: NotificationRequest, userId: number): Promise<void>
```

发布通知给指定的用户（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [publish](arkts-notification-notificationmanager-publish-f.md)(request: NotificationRequest, userId: number)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function publish(request: NotificationRequest, userId: number): Promise<void>--><!--Device-notification-function publish(request: NotificationRequest, userId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationrequest-i.md) | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

<!--Del-->
**示例**

```TypeScript
import NotificationManager from '@ohos.notificationManager';
import Base from '@ohos.base';

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

let userId: number = 1;

Notification.publish(notificationRequest, userId).then(() => {
  console.info("publish success");
}).catch((err: Base.BusinessError) => {
  console.error(`publish failed, code is ${err}`);
});
```

<!--DelEnd-->
