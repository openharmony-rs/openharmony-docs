# setAdditionalConfig（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## setAdditionalConfig

```TypeScript
function setAdditionalConfig(key: string, value: string): Promise<number>
```

设置通知的系统附加配置信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 附加配置键。目前仅支持`RING_TRUSTLIST_PKG`，表示应用支持使用<br/>[自定义铃声](arkts-notification-notificationrequest-i.md#NotificationRequest)。 |
| value | string | 是 | 附加配置值。参数示例：[bundleName1,bundleName2]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回0表示设置成功，返回其他值表示设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setAdditionalConfig('RING_TRUSTLIST_PKG','[bundleName1,bundleName2]').then((data: number) => {
  console.info(`setAdditionalConfig success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`setAdditionalConfig failed, code is ${err.code}, message is ${err.message}`);
});

```

