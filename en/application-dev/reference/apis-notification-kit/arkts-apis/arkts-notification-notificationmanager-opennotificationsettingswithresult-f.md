# openNotificationSettingsWithResult

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## openNotificationSettingsWithResult

```TypeScript
function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>
```

Brings up the [notification setting](../../../notification/notification-glossary.md#notification-setting) page of the application. The page is presented in semi-modal form and can be used to set the notification switch, [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode), and so on. This API uses a promise to return the result, and returns the status set by the user when the semi-modal window is closed.

Unlike [openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md), this API returns a [NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md) object when the semi-modal window is closed. You can determine whether the user has enabled the notification permission based on the returned result, thereby deciding subsequent logic.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>--><!--Device-notificationManager-function openNotificationSettingsWithResult(context: UIAbilityContext): Promise<NotificationSetting>-End-->

**System capability:** SystemCapability.Notification.NotificationSettings

**See also:**

[requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-4) requests notification to be enabled for this application.

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) checks whether notification is enabled for the specified application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Ability context bound to the notification settings page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md)&gt; | Promise used to return the notification settings of this application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600018](../errorcode-notification.md#1600018-notification-settings-page-already-displayed) | The notification settings window is already displayed. |

**Examples**

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
