# publish

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## publish

```TypeScript
function publish(request: NotificationRequest, callback: AsyncCallback<void>): void
```

发布通知。使用callback异步回调。

发布通知后，通知将以通知卡片的形式展示在设备的通知中心、状态栏等位置。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知，实现通知的更新效果。

**起始版本：** 9

<!--Device-notificationManager-function publish(request: NotificationRequest, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function publish(request: NotificationRequest, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | 是 | 设置发布通知的内容和相关配置信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当发布通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-通知渠道关闭) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist.<br>**适用版本：** 11+ |
| [1600009](../errorcode-notification.md#1600009-通知发布频度超过限制) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-没有相关权限) | No permission.<br>**适用版本：** 11+ |
| [1600015](../errorcode-notification.md#1600015-当前通知状态不支持重复配置) | The current notification status does not support duplicate configurations.<br>**适用版本：** 11+ |
| [1600016](../errorcode-notification.md#1600016-本次更新的通知版本太低) | The notification version for this update is too low.<br>**适用版本：** 11+ |
| [1600020](../errorcode-notification.md#1600020-不允许权限管控名单中的应用发布通知) | The application is not allowed to send notifications due to permission settings.<br>**适用版本：** 12+ |
| [1600029](../errorcode-notification.md#1600029-系统无法找到实况窗卡片自定义扩展区的extensionability) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**适用版本：** 26.0.0+ |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-无法连接到服务器) | Network unreachable.<br>**适用版本：** 11+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// publish回调
let publishCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in publishing notification.`);
  }
}
// 通知Request对象
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest, publishCallback);

```


## publish

```TypeScript
function publish(request: NotificationRequest): Promise<void>
```

发布通知。使用Promise异步回调。

发布通知后，通知将以通知卡片的形式展示在设备的通知中心、状态栏等位置。如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知，实现通知的更新效果。

**起始版本：** 9

<!--Device-notificationManager-function publish(request: NotificationRequest): Promise<void>--><!--Device-notificationManager-function publish(request: NotificationRequest): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | 是 | 设置发布通知的内容和相关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-通知渠道关闭) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist.<br>**适用版本：** 11+ |
| [1600009](../errorcode-notification.md#1600009-通知发布频度超过限制) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-没有相关权限) | No permission.<br>**适用版本：** 11+ |
| [1600015](../errorcode-notification.md#1600015-当前通知状态不支持重复配置) | The current notification status does not support duplicate configurations.<br>**适用版本：** 11+ |
| [1600016](../errorcode-notification.md#1600016-本次更新的通知版本太低) | The notification version for this update is too low.<br>**适用版本：** 11+ |
| [1600020](../errorcode-notification.md#1600020-不允许权限管控名单中的应用发布通知) | The application is not allowed to send notifications due to permission settings.<br>**适用版本：** 12+ |
| [1600029](../errorcode-notification.md#1600029-系统无法找到实况窗卡片自定义扩展区的extensionability) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**适用版本：** 26.0.0+ |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-无法连接到服务器) | Network unreachable.<br>**适用版本：** 11+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 通知Request对象
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest).then(() => {
  console.info(`Succeeded in publishing notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
});


```

