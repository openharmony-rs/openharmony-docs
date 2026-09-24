# requestEnableNotification

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

Requests notification to be enabled for this application. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled.<br>**Applicable version:** 11 and later |
| [1600013](../errorcode-notification.md#1600013-notification-pop-up-window-displayed) | A notification dialog box is already displayed.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let requestEnableNotificationCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`requestEnableNotification success`);
  }
};
notificationManager.requestEnableNotification(requestEnableNotificationCallback);
```


<a id="requestenablenotification-1"></a>

## requestEnableNotification

```TypeScript
function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback<void>): void
```

Requests notification to be enabled for this application. You can call this API to display a dialog box prompting the user to enable notification for your application before publishing a notification. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - This API can be called only after the application UI is loaded (that is,[loadContent](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#loadcontent) is successfully called).
> 
> - When an application uses **requestEnableNotification()** to display a dialog box for notification authorization and the user rejects the authorization, the application cannot use this API to open the dialog box again. However , it can call [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md)to open the notification management dialog box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**See also:**

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md#isnotificationenabled-2) checks whether notification is enabled for a specified user.

[openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md) Opens the notification settings page of the application, which is presented in a semi-modal window and can be used to set notification switches, notification reminder methods, etc.

[openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md) opens the notification settings page of the application, which is displayed in semi-modal mode and can be used to set the notification enabling and notification mode.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Ability context bound to the notification dialog box. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled.<br>**Applicable version:** 11 and later |
| [1600013](../errorcode-notification.md#1600013-notification-pop-up-window-displayed) | A notification dialog box is already displayed.<br>**Applicable version:** 11 and later |

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
      let requestEnableNotificationCallback = (err: BusinessError): void => {
        if (err) {
          hilog.error(0x0000, 'testTag', `[ANS] requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
        } else {
          hilog.info(0x0000, 'testTag', `[ANS] requestEnableNotification success`);
        }
      };
      notificationManager.requestEnableNotification(this.context, requestEnableNotificationCallback);
    });
  }
}
```


<a id="requestenablenotification-2"></a>

## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

Requests notification to be enabled for this application. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled.<br>**Applicable version:** 11 and later |
| [1600013](../errorcode-notification.md#1600013-notification-pop-up-window-displayed) | A notification dialog box is already displayed.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.requestEnableNotification().then(() => {
  console.info(`requestEnableNotification success`);
}).catch((err: BusinessError) => {
  console.error(`requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
});
```


<a id="requestenablenotification-3"></a>

## requestEnableNotification

```TypeScript
function requestEnableNotification(context: UIAbilityContext): Promise<void>
```

Requests notification to be enabled for this application. You can call this API to display a dialog box prompting the user to enable notification for your application before publishing a notification. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API can be called only after the application UI is loaded (that is,[loadContent](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#loadcontent) is successfully called).
> 
> - When an application uses **requestEnableNotification()** to display a dialog box for notification authorization and the user rejects the authorization, the application cannot use this API to open the dialog box again. However , it can call [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md)to open the notification management dialog box.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**See also:**

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md#isnotificationenabled-2) checks whether notification is enabled for a specified user.

[openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md) Opens the notification settings page of the application, which is presented in a semi-modal window and can be used to set notification switches, notification reminder methods, etc.

[openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md) opens the notification settings page of the application, which is displayed in semi-modal mode and can be used to set the notification enabling and notification mode.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Ability context bound to the notification dialog box. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled.<br>**Applicable version:** 11 and later |
| [1600013](../errorcode-notification.md#1600013-notification-pop-up-window-displayed) | A notification dialog box is already displayed.<br>**Applicable version:** 11 and later |

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
      notificationManager.requestEnableNotification(this.context).then(() => {
        hilog.info(0x0000, 'testTag', `[ANS] requestEnableNotification success`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `[ANS] requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}
```
