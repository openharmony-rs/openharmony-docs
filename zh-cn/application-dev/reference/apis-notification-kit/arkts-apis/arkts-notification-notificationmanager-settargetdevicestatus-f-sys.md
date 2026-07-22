# setTargetDeviceStatus（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setTargetDeviceStatus

```TypeScript
function setTargetDeviceStatus(deviceType: string, status: number): Promise<void>
```

设置设备配对成功后的状态。当发布通知时，会根据各个设备的状态来确定当前设备的通知提醒方式。

**起始版本：** 18

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setTargetDeviceStatus(deviceType: string, status: long): Promise<void>--><!--Device-notificationManager-function setTargetDeviceStatus(deviceType: string, status: long): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | string | 是 | 设备类型。当前仅支持`headset`（可穿戴式音频设备）、`liteWearable`（轻量级智能穿戴设备）、`wearable`（智能穿戴设备）、`glasses`（智能眼镜设备）、`current`（本设备）。 |
| status | number | 是 | 设备状态。<br>- bit0：设备是否正在被使用。0表示未使用，1表示使用中。<br>- bit1：当前设备使用者是否为机主。0表示为非机主，1表示为机主。<br>- bit2：设备是否处于勿扰模式。0表示处于非勿扰模式，1表示处于勿扰模式。 |

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

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.setTargetDeviceStatus("current", 1).then(() => {
  console.info(`Succeeded in setting target device status.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set target device status. Code is ${err.code}, message is ${err.message}`);
});

```

