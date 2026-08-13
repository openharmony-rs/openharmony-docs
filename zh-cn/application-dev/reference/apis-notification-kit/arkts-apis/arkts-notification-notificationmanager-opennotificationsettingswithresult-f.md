# openNotificationSettingsWithResult

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## openNotificationSettingsWithResult

```TypeScript
function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>
```

拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、 通知提醒方式等。使用Promise异步回调，当半模态窗口关闭时返回用户设置的状态。 与openNotificationSettings相比，此接口在半模态窗口关闭时返回 NotificationSetting对象，开发者可根据返回结果判断用户是否开启了通知 权限，从而决定后续逻辑。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>--><!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>-End-->

**系统能力：** SystemCapability.Notification.NotificationSettings

**参见：**

requestEnableNotification 请求通知使能。

isNotificationEnabled 查询当前应用通知授权状态。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | 通知设置页面绑定Ability的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md)&gt; | Promise对象，返回此应用的通知设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600018](../errorcode-notification.md#1600018-通知设置页面已经拉起) | The notification settings window is already displayed. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err) ?? ''}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data) ?? ''}`);
      notificationManager.openNotificationSettingsWithResult(this.context).then((data) => {
        hilog.info(0x0000, 'testTag', `[ANS] openNotificationSettingsWithResult success, data: ${JSON.stringify(data)}`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `[ANS] openNotificationSettingsWithResult failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause: ${JSON.stringify(err) ?? ''}`);
        return;
      }
      hilog.info(0x0000, 'testTag', `Succeeded in loading the content. Data: ${JSON.stringify(data) ?? ''}`);
      notificationManager.openNotificationSettingsWithResult(this.context).then((data) => {
        hilog.info(0x0000, 'testTag', `[ANS] openNotificationSettingsWithResult success, data: ${JSON.stringify(data)}`);
      }).catch((err: Error) : void => {
        let error: BusinessError = err as BusinessError;
        hilog.error(0x0000, 'testTag', `[ANS] openNotificationSettingsWithResult failed, code is ${error.code}, message is ${error.message}`);
      });
    });
  }
}
```

