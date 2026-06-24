# publish

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## publish

```TypeScript
function publish(request: NotificationRequest, callback: AsyncCallback<void>): void
```

发布通知。使用callback异步回调。

如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 设置发布通知的内容和相关配置信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当发布通知成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600004](../../errorcode-universal.md#1600004-Notification) | Notification disabled. |
| [1600005](../../errorcode-universal.md#1600005-Notification) | Notification slot disabled. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist.&lt;br&gt;**适用版本：** 11+ |
| [1600009](../../errorcode-universal.md#1600009-The) | The notification sending frequency reaches the upper limit. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600014](../../errorcode-universal.md#1600014-No) | No permission.&lt;br&gt;**适用版本：** 11+ |
| [1600015](../../errorcode-universal.md#1600015-The) | The current notification status does not support duplicate<br/>configurations.&lt;br&gt;**适用版本：** 11+ |
| [1600016](../../errorcode-universal.md#1600016-The) | The notification version for this update is too low.&lt;br&gt;**适用版本：** 11+ |
| [1600020](../../errorcode-universal.md#1600020-The) | The application is not allowed to send notifications due to permission<br/>settings.&lt;br&gt;**适用版本：** 12+ |
| [2300007](../../errorcode-universal.md#2300007-Network) | Network unreachable.&lt;br&gt;**适用版本：** 11+ |

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

如果新发布通知与已发布通知的ID和标签都相同，则新通知将取代原有通知。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 设置发布通知的内容和相关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600004](../../errorcode-universal.md#1600004-Notification) | Notification disabled. |
| [1600005](../../errorcode-universal.md#1600005-Notification) | Notification slot disabled. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist.&lt;br&gt;**适用版本：** 11+ |
| [1600009](../../errorcode-universal.md#1600009-The) | The notification sending frequency reaches the upper limit. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600014](../../errorcode-universal.md#1600014-No) | No permission.&lt;br&gt;**适用版本：** 11+ |
| [1600015](../../errorcode-universal.md#1600015-The) | The current notification status does not support duplicate<br/>configurations.&lt;br&gt;**适用版本：** 11+ |
| [1600016](../../errorcode-universal.md#1600016-The) | The notification version for this update is too low.&lt;br&gt;**适用版本：** 11+ |
| [1600020](../../errorcode-universal.md#1600020-The) | The application is not allowed to send notifications due to permission<br/>settings.&lt;br&gt;**适用版本：** 12+ |
| [2300007](../../errorcode-universal.md#2300007-Network) | Network unreachable.&lt;br&gt;**适用版本：** 11+ |

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

