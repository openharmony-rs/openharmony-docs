# publishAsBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
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
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-The) | The device does not support geofencing.&lt;br&gt;**适用版本：** 23+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600004](../../errorcode-universal.md#1600004-Notification) | Notification disabled. |
| [1600005](../../errorcode-universal.md#1600005-Notification) | Notification slot disabled. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [1600009](../../errorcode-universal.md#1600009-The) | The notification sending frequency reaches the upper limit. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600015](../../errorcode-universal.md#1600015-The) | The current notification status does not support duplicate configurations. |
| [1600016](../../errorcode-universal.md#1600016-The) | The notification version for this update is too low. |
| [1600020](../../errorcode-universal.md#1600020-The) | The application is not allowed to send notifications due to permission<br/>settings. |
| [1600025](../../errorcode-universal.md#1600025-Geofencing) | Geofencing disabled.&lt;br&gt;**适用版本：** 23+ |
| [1600026](../../errorcode-universal.md#1600026-The) | The location switch is off.&lt;br&gt;**适用版本：** 23+ |
| [1600027](../../errorcode-universal.md#1600027-The) | The "Awareness & suggestions" switch of the location-based service is<br/>off.&lt;br&gt;**适用版本：** 23+ |
| [2300007](../../errorcode-universal.md#2300007-Network) | Network unreachable. |

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
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-The) | The device does not support geofencing.&lt;br&gt;**适用版本：** 23+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600004](../../errorcode-universal.md#1600004-Notification) | Notification disabled. |
| [1600005](../../errorcode-universal.md#1600005-Notification) | Notification slot disabled. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [1600009](../../errorcode-universal.md#1600009-The) | The notification sending frequency reaches the upper limit. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600015](../../errorcode-universal.md#1600015-The) | The current notification status does not support duplicate configurations. |
| [1600016](../../errorcode-universal.md#1600016-The) | The notification version for this update is too low. |
| [1600020](../../errorcode-universal.md#1600020-The) | The application is not allowed to send notifications due to permission<br/>settings. |
| [1600025](../../errorcode-universal.md#1600025-Geofencing) | Geofencing disabled.&lt;br&gt;**适用版本：** 23+ |
| [1600026](../../errorcode-universal.md#1600026-The) | The location switch is off.&lt;br&gt;**适用版本：** 23+ |
| [1600027](../../errorcode-universal.md#1600027-The) | The "Awareness & suggestions" switch of the location-based service is<br/>off.&lt;br&gt;**适用版本：** 23+ |
| [2300007](../../errorcode-universal.md#2300007-Network) | Network unreachable. |

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
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-The) | The device does not support geofencing.&lt;br&gt;**适用版本：** 23+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |
| [1600004](../../errorcode-universal.md#1600004-Notification) | Notification disabled. |
| [1600005](../../errorcode-universal.md#1600005-Notification) | Notification slot disabled. |
| [1600007](../../errorcode-universal.md#1600007-The) | The notification does not exist. |
| [1600008](../../errorcode-universal.md#1600008-The) | The user does not exist. |
| [1600009](../../errorcode-universal.md#1600009-The) | The notification sending frequency reaches the upper limit. |
| [1600012](../../errorcode-universal.md#1600012-No) | No memory space. |
| [1600015](../../errorcode-universal.md#1600015-The) | The current notification status does not support duplicate configurations. |
| [1600016](../../errorcode-universal.md#1600016-The) | The notification version for this update is too low. |
| [1600020](../../errorcode-universal.md#1600020-The) | The application is not allowed to send notifications due to permission<br/>settings. |
| [1600025](../../errorcode-universal.md#1600025-Geofencing) | Geofencing disabled.&lt;br&gt;**适用版本：** 23+ |
| [1600026](../../errorcode-universal.md#1600026-The) | The location switch is off.&lt;br&gt;**适用版本：** 23+ |
| [1600027](../../errorcode-universal.md#1600027-The) | The "Awareness & suggestions" switch of the location-based service is<br/>off.&lt;br&gt;**适用版本：** 23+ |
| [2300007](../../errorcode-universal.md#2300007-Network) | Network unreachable. |

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

