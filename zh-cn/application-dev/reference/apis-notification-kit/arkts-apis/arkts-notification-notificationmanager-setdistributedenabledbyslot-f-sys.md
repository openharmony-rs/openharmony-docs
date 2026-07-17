# setDistributedEnabledBySlot（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setDistributedEnabledBySlot

```TypeScript
function setDistributedEnabledBySlot(slot: SlotType, deviceType: string, enabled: boolean): Promise<void>
```

设置指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setDistributedEnabledBySlot(slot: SlotType, deviceType: string, enabled: boolean): Promise<void>--><!--Device-notificationManager-function setDistributedEnabledBySlot(slot: SlotType, deviceType: string, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | [SlotType](arkts-notification-notificationmanager-slottype-e-sys.md) | 是 | 通知渠道类型。 |
| deviceType | string | 是 | 设备类型。<br>从API version 18开始，支持的设备类型如下：<br>- headset（可穿戴式音频设备）。<br>- liteWearable（轻量级智能穿戴设备）。<br>- wearable（智能穿戴设备）。<br>从API version 20开始，支持的设备类型如下：<br>- headset（可穿戴式音频设备）。<br>- liteWearable（轻量级智能穿戴设备）。<br>- wearable（智能穿戴设备）。<br>- current（本设备）。<br>- 2in1（PC设备）。<br>- tablet（平板）。 |
| enabled | boolean | 是 | 是否开启通知跨设备协同开关。取值为true表示打开，取值为false表示关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let slot: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
let deviceType: string = 'wearable';
let enabled: boolean = true;

notificationManager.setDistributedEnabledBySlot(slot, deviceType, enabled).then(() => {
    hilog.info(0x0000, 'testTag', '%{public}s', `setDistributedEnabledBySlot success.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', '%{public}s', `setDistributedEnabledBySlot failed, code is ${err.code}, message is ${err.message}`);
});

```

