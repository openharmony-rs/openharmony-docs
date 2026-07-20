# openNotificationSettingsWithResult

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="opennotificationsettingswithresult"></a>
## openNotificationSettingsWithResult

```TypeScript
function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>
```

拉起应用的通知设置界面，该页面以半模态形式呈现，可用于设置通知开关、通知提醒方式等。使用Promise异步回调，当半模态窗口关闭时返回用户设置的状态。

与openNotificationSettings相比，此接口在半模态窗口关闭时返回NotificationSetting对象，开发者可根据返回结果判断用户是否开启了通知权限，从而决定后续逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>--><!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>-End-->

**系统能力：** SystemCapability.Notification.NotificationSettings

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 是 | 通知设置页面绑定Ability的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSetting&gt; | Promise对象，返回此应用程序的通知设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600018](../errorcode-notification.md#1600018-通知设置页面已经拉起) | The notification settings window is already displayed. |

**示例：**

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

