# isDistributedEnabledBySlot（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isDistributedEnabledBySlot

```TypeScript
function isDistributedEnabledBySlot(slot: SlotType, deviceType: string): Promise<boolean>
```

查询指定渠道的通知是否支持通知跨设备协同至指定类型设备。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isDistributedEnabledBySlot(slot: SlotType, deviceType: string): Promise<boolean>--><!--Device-notificationManager-function isDistributedEnabledBySlot(slot: SlotType, deviceType: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slot | SlotType | 是 | 通知渠道类型。 |
| deviceType | string | 是 | 设备类型。&lt;br&gt;从API version 18开始，支持的设备类型如下：&lt;br&gt;- headset（可穿戴式音频设备）。&lt;br&gt;- liteWearable（轻量级智 能穿戴设备）。&lt;br&gt;- wearable（智能穿戴设备）。&lt;br&gt;从API version 20开始，支持的设备类型如下：&lt;br&gt;- headset（可穿戴式音频设备）。&lt;br&gt;- liteWearable（轻量级智能穿 戴设备）。&lt;br&gt;- wearable（智能穿戴设备）。&lt;br&gt;- current（本设备）。&lt;br&gt;- 2in1（PC设备）。&lt;br&gt;- tablet（平板）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示指定渠道的通知支持通知跨设备协同至指定类型设备；返回false表示指定渠道的通知不支持通知跨设备协同至指定类型设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let slot: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
let deviceType: string = 'wearable';

notificationManager.isDistributedEnabledBySlot(slot, deviceType).then((data: boolean) => {
    hilog.info(0x0000, 'testTag', '%{public}s', `isDistributedEnabledBySlot success.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', '%{public}s', `isDistributedEnabledBySlot failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slot: notificationManager.SlotType = notificationManager.SlotType.SOCIAL_COMMUNICATION;
let deviceType: string = 'wearable';

notificationManager.isDistributedEnabledBySlot(slot, deviceType).then((data: boolean) => {
    console.info('isDistributedEnabledBySlot success.');
}).catch((err: Error): void => {
    let error: BusinessError = err as BusinessError;
    console.error(`isDistributedEnabledBySlot failed, code is ${error.code}, message is ${error.message}`);
});
```

