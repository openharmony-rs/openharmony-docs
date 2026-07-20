# setRingtoneInfoByBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="setringtoneinfobybundle"></a>
## setRingtoneInfoByBundle

```TypeScript
function setRingtoneInfoByBundle(bundle: BundleOption, ringtoneInfo: RingtoneInfo): Promise<void>
```

设置应用自定义铃声信息。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setRingtoneInfoByBundle(bundle: BundleOption, ringtoneInfo: RingtoneInfo): Promise<void>--><!--Device-notificationManager-function setRingtoneInfoByBundle(bundle: BundleOption, ringtoneInfo: RingtoneInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| ringtoneInfo | [RingtoneInfo](arkts-notification-notificationmanager-ringtoneinfo-i-sys.md) | 是 | 自定义铃声信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The specified bundle is invalid. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    try {
      let bundle: notificationManager.BundleOption = {
        bundle: "bundleName",
      };
      let ringtoneInfo: notificationManager.RingtoneInfo = {
        ringtoneType: notificationManager.RingtoneType.RINGTONE_TYPE_SYSTEM,
        ringtoneTitle: "ringtoneName",
        ringtoneFileName: "ringtonePath",
        ringtoneUri: "ringtoneUri",
      }
      notificationManager.setRingtoneInfoByBundle(bundle, ringtoneInfo).then(() => {
        console.info(`setRingtoneInfoByBundle bundle: ${JSON.stringify(bundle)}', ringtoneInfoJSON：' ${JSON.stringify(ringtoneInfo)}`);
      }).catch((err: BusinessError) => {
         console.error(`setRingtoneInfoByBundle failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      console.error(`setRingtoneInfoByBundle failed, code is ${err.code}, message is ${err.message}`);
    }
  }
}

```

