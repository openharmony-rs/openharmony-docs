# setSmartReminderEnabled（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setSmartReminderEnabled

```TypeScript
function setSmartReminderEnabled(deviceType: string, enable: boolean): Promise<void>
```

设置设备是否与其他设备协同智能提醒。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | string | 是 | 设备类型。 |
| enable | boolean | 是 | 指定应用是否支持设备是否与其他设备协同智能提醒（true：支持，false：不支持）。 |

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
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600010](../errorcode-notification.md#1600010-分布式操作失败) | Distributed operation failed. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let deviceType: string = "phone";
let enable: boolean = true;
notificationManager.setSmartReminderEnabled(deviceType, enable).then(() => {
    console.info("setSmartReminderEnabled success");
}).catch((err: BusinessError) => {
    console.error(`setSmartReminderEnabled failed, code is ${err.code}, message is ${err.message}`);
});

```

