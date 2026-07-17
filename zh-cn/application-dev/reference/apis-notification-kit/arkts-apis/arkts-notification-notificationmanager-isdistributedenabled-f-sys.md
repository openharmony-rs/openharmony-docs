# isDistributedEnabled（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(deviceType: string): Promise<boolean>
```

查询设备是否支持跨设备协同通知。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isDistributedEnabled(deviceType: string): Promise<boolean>--><!--Device-notificationManager-function isDistributedEnabled(deviceType: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceType | string | 是 | 设备类型。当前仅支持以下类型：<br>- headset（可穿戴式音频设备）。<br>- liteWearable（轻量级智能穿戴设备）。<br>- wearable（智能穿戴设备）。<br>- current（本设备）。<br>- 2in1（PC设备）。<br>- tablet（平板）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | 返回设备是否支持跨设备协同通知的结果，返回true表示支持；返回false表示不支持。Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    try {
      let deviceType: string = "wearable";
      notificationManager.isDistributedEnabled(deviceType).then((data: boolean) => {
        console.info('isDistributedEnabled succeeded, result = ' + data);
      }).catch((err: BusinessError) => {
        console.error(`isDistributedEnabled failed. Code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      console.error(`isDistributedEnabled failed. Code is ${err.code}, message is ${err.message}`);
    }
  }
}

```

