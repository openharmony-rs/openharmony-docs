# requestEnableNotification

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

当前应用请求通知使能。使用callback异步回调。

> **说明：**  
>  
> 从API version 9开始支持，从API version 12开始废弃，建议使用有context入参的  
> [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-2)  
> 替代。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1)

<!--Device-notificationManager-function requestEnableNotification(callback: AsyncCallback<void>): void--><!--Device-notificationManager-function requestEnableNotification(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当应用请求通知使能成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled.<br>**适用版本：** 11+ |
| [1600013](../errorcode-notification.md#1600013-通知弹窗已弹出) | A notification dialog box is already displayed.<br>**适用版本：** 11+ |

**示例：**

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


## requestEnableNotification

```TypeScript
function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback<void>): void
```

应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用callback异步回调。

> **说明：**  
>  
> - 仅当应用界面加载完成后（即调用  
> [loadContent](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#loadcontent-1)成功），方可使用该接口  
> 。  
>  
> - 在使用该接口拉起通知授权弹窗后，如果用户拒绝授权，将无法使用该接口再次拉起弹窗。开发者可以调用  
> [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1)二次申请授权，拉起通知管理弹窗  
> 。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 是 | 通知弹窗绑定Ability的上下文。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当应用通过弹窗获取用户授权成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled.<br>**适用版本：** 11+ |
| [1600013](../errorcode-notification.md#1600013-通知弹窗已弹出) | A notification dialog box is already displayed.<br>**适用版本：** 11+ |

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


## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

当前应用请求通知使能。使用Promise异步回调。

> **说明：**  
>  
> 从API version 9开始支持，从API version 12开始废弃，建议使用有context入参的  
> [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-4)替代。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1)

<!--Device-notificationManager-function requestEnableNotification(): Promise<void>--><!--Device-notificationManager-function requestEnableNotification(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled.<br>**适用版本：** 11+ |
| [1600013](../errorcode-notification.md#1600013-通知弹窗已弹出) | A notification dialog box is already displayed.<br>**适用版本：** 11+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.requestEnableNotification().then(() => {
  console.info(`requestEnableNotification success`);
}).catch((err: BusinessError) => {
  console.error(`requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
});

```


## requestEnableNotification

```TypeScript
function requestEnableNotification(context: UIAbilityContext): Promise<void>
```

应用需要获取用户授权才能发送通知。在通知发布前调用该接口，可以拉起通知授权弹窗，让用户选择是否允许发送通知。使用Promise异步回调。

> **说明：**  
>  
> - 仅当应用界面加载完成后（即调用  
> [loadContent](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#loadcontent-1)成功），方可使用该接口  
> 。  
>  
> - 在使用该接口拉起通知授权弹窗后，如果用户拒绝授权，将无法使用该接口再次拉起弹窗。开发者可以调用  
> [openNotificationSettingsWithResult](arkts-notification-notificationmanager-opennotificationsettingswithresult-f.md#opennotificationsettingswithresult-1)二次申请授权，拉起通知管理弹窗  
> 。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function requestEnableNotification(context: UIAbilityContext): Promise<void>--><!--Device-notificationManager-function requestEnableNotification(context: UIAbilityContext): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 是 | 通知弹窗绑定的Ability上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-通知开关关闭) | Notification disabled.<br>**适用版本：** 11+ |
| [1600013](../errorcode-notification.md#1600013-通知弹窗已弹出) | A notification dialog box is already displayed.<br>**适用版本：** 11+ |

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
      notificationManager.requestEnableNotification(this.context).then(() => {
        hilog.info(0x0000, 'testTag', `[ANS] requestEnableNotification success`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `[ANS] requestEnableNotification failed, code is ${err.code}, message is ${err.message}`);
      });
    });
  }
}

```

