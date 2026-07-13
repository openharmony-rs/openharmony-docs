# publishAsBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## publishAsBundle

```TypeScript
function publishAsBundle(
    request: NotificationRequest,
    representativeBundle: string,
    userId: number,
    callback: AsyncCallback<void>
  ): void
```

发布代理通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| representativeBundle | string | 是 | 被代理应用的包名。 |
| userId | number | 是 | 用户ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 发布代理通知的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The device does not support geofencing.<br>**适用版本：** 23+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-通知渠道关闭) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-通知发布频度超过限制) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-没有相关权限) | The right of liveView is not enabled.<br>**适用版本：** 26.0.0+ |
| [1600015](../errorcode-notification.md#1600015-当前通知状态不支持重复配置) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-本次更新的通知版本太低) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-不允许权限管控名单中的应用发布通知) | The application is not allowed to send notifications due to permissionsettings. |
| [1600025](../errorcode-notification.md#1600025-地理围栏开关关闭) | Geofencing disabled.<br>**适用版本：** 23+ |
| [1600026](../errorcode-notification.md#1600026-位置功能开关关闭) | The location switch is off.<br>**适用版本：** 23+ |
| [1600027](../errorcode-notification.md#1600027-位置系统服务的感知与提醒开关关闭) | The "Awareness & suggestions" switch of the location-based service isoff.<br>**适用版本：** 23+ |
| [1600029](../errorcode-notification.md#1600029-系统无法找到实况窗卡片自定义扩展区的extensionability) | The system failed to find the ExtensionAbility instance for thecustom Live View widget template.<br>**适用版本：** 26.0.0+ |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-无法连接到服务器) | Network unreachable. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// publishAsBundle回调
let callback = (err: BusinessError): void => {
    if (err) {
        console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("publishAsBundle success");
    }
}
// 被代理应用的包名
let representativeBundle: string = "com.example.demo";
// 用户ID，使用时需替换为真实的userId。
let userId: number = 100;
// NotificationRequest对象
let request: notificationManager.NotificationRequest = {
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
notificationManager.publishAsBundle(request, representativeBundle, userId, callback);

```


## publishAsBundle

```TypeScript
function publishAsBundle(request: NotificationRequest, representativeBundle: string, userId: number): Promise<void>
```

发布代理通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| representativeBundle | string | 是 | 被代理应用的包名。 |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The device does not support geofencing.<br>**适用版本：** 23+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-通知渠道关闭) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-通知发布频度超过限制) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-没有相关权限) | The right of liveView is not enabled.<br>**适用版本：** 26.0.0+ |
| [1600015](../errorcode-notification.md#1600015-当前通知状态不支持重复配置) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-本次更新的通知版本太低) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-不允许权限管控名单中的应用发布通知) | The application is not allowed to send notifications due to permissionsettings. |
| [1600025](../errorcode-notification.md#1600025-地理围栏开关关闭) | Geofencing disabled.<br>**适用版本：** 23+ |
| [1600026](../errorcode-notification.md#1600026-位置功能开关关闭) | The location switch is off.<br>**适用版本：** 23+ |
| [1600027](../errorcode-notification.md#1600027-位置系统服务的感知与提醒开关关闭) | The "Awareness & suggestions" switch of the location-based service isoff.<br>**适用版本：** 23+ |
| [1600029](../errorcode-notification.md#1600029-系统无法找到实况窗卡片自定义扩展区的extensionability) | The system failed to find the ExtensionAbility instance for thecustom Live View widget template.<br>**适用版本：** 26.0.0+ |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-无法连接到服务器) | Network unreachable. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 被代理应用的包名
let representativeBundle: string = "com.example.demo";
// 用户ID，使用时需替换为真实的userId。
let userId: number = 100;
// NotificationRequest对象
let request: notificationManager.NotificationRequest = {
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
notificationManager.publishAsBundle(request, representativeBundle, userId).then(() => {
    console.info("publishAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
});

```


## publishAsBundle

```TypeScript
function publishAsBundle(representativeBundle: BundleOption, request: NotificationRequest): Promise<void>
```

发布代理通知。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| representativeBundle | BundleOption | 是 | 被代理应用的包信息。 |
| request | NotificationRequest | 是 | 用于设置要发布通知的内容和相关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The device does not support geofencing.<br>**适用版本：** 23+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-通知渠道关闭) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [1600008](../errorcode-notification.md#1600008-用户不存在) | The user does not exist. |
| [1600009](../errorcode-notification.md#1600009-通知发布频度超过限制) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-没有相关权限) | The right of liveView is not enabled.<br>**适用版本：** 26.0.0+ |
| [1600015](../errorcode-notification.md#1600015-当前通知状态不支持重复配置) | The current notification status does not support duplicate configurations. |
| [1600016](../errorcode-notification.md#1600016-本次更新的通知版本太低) | The notification version for this update is too low. |
| [1600020](../errorcode-notification.md#1600020-不允许权限管控名单中的应用发布通知) | The application is not allowed to send notifications due to permissionsettings. |
| [1600025](../errorcode-notification.md#1600025-地理围栏开关关闭) | Geofencing disabled.<br>**适用版本：** 23+ |
| [1600026](../errorcode-notification.md#1600026-位置功能开关关闭) | The location switch is off.<br>**适用版本：** 23+ |
| [1600027](../errorcode-notification.md#1600027-位置系统服务的感知与提醒开关关闭) | The "Awareness & suggestions" switch of the location-based service isoff.<br>**适用版本：** 23+ |
| [1600029](../errorcode-notification.md#1600029-系统无法找到实况窗卡片自定义扩展区的extensionability) | The system failed to find the ExtensionAbility instance for thecustom Live View widget template.<br>**适用版本：** 26.0.0+ |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-无法连接到服务器) | Network unreachable. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 被代理应用的包信息
let representativeBundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
// NotificationRequest对象
let request: notificationManager.NotificationRequest = {
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
notificationManager.publishAsBundle(representativeBundle, request).then(() => {
    console.info("publishAsBundle success");
}).catch((err: BusinessError) => {
    console.error(`publishAsBundle failed, code is ${err.code}, message is ${err.message}`);
});

```

