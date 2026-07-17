# isSupportDoNotDisturbMode（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isSupportDoNotDisturbMode

```TypeScript
function isSupportDoNotDisturbMode(callback: AsyncCallback<boolean>): void
```

查询是否支持免打扰功能。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isSupportDoNotDisturbMode(callback: AsyncCallback<boolean>): void--><!--Device-notificationManager-function isSupportDoNotDisturbMode(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 查询是否支持免打扰功能回调函数（true：支持，false：不支持）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let isSupportDoNotDisturbModeCallback = (err: BusinessError, data: boolean): void => {
    if (err) {
        console.error(`isSupportDoNotDisturbMode failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info(`isSupportDoNotDisturbMode success, data: ${JSON.stringify(data)}`);
    }
}

notificationManager.isSupportDoNotDisturbMode(isSupportDoNotDisturbModeCallback);

```


## isSupportDoNotDisturbMode

```TypeScript
function isSupportDoNotDisturbMode(): Promise<boolean>
```

查询是否支持免打扰功能。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isSupportDoNotDisturbMode(): Promise<boolean>--><!--Device-notificationManager-function isSupportDoNotDisturbMode(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | 以Promise形式返回获取是否支持免打扰功能的结果（true：支持，false：不支持）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.isSupportDoNotDisturbMode().then((data: boolean) => {
    console.info(`isSupportDoNotDisturbMode success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isSupportDoNotDisturbMode failed, code is ${err.code}, message is ${err.message}`);
});

```

