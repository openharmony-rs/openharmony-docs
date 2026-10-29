# isSupportTemplate

## Modules to Import

```TypeScript
```

## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void
```

Before publishing a notification using [NotificationTemplate](arkts-notification-notificationtemplate-i.md), you can call this API to check whether the corresponding notification template is supported. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate-1)(templateName: string, callback: AsyncCallback&lt;boolean&gt;)

<!--Device-notification-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void--><!--Device-notification-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateName | string | Yes | Template name. Currently, only **downloadTemplate** is supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let templateName: string = 'downloadTemplate';
function isSupportTemplateCallback(err: Base.BusinessError, data: boolean) {
  if (err) {
    console.error("isSupportTemplate failed " + JSON.stringify(err));
  } else {
    console.info("isSupportTemplate success");
  }
}

Notification.isSupportTemplate(templateName, isSupportTemplateCallback);
```


## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string): Promise<boolean>
```

Checks whether a specified template is supported before using [NotificationTemplate](arkts-notification-notificationtemplate-i.md) to publish a notification. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSupportTemplate](arkts-notification-notificationmanager-issupporttemplate-f.md#issupporttemplate-2)(templateName: string)

<!--Device-notification-function isSupportTemplate(templateName: string): Promise<boolean>--><!--Device-notification-function isSupportTemplate(templateName: string): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateName | string | Yes | Template name. Currently, only **downloadTemplate** is supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let templateName: string = 'downloadTemplate';
Notification.isSupportTemplate(templateName).then((data: boolean) => {
  console.info("isSupportTemplate success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isSupportTemplate failed, code is ${err}`);
});
```
