# supportDoNotDisturbMode (System API)

## Modules to Import

```TypeScript
```

## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void
```

Checks whether DND mode is supported. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md#issupportdonotdisturbmode-1)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void--><!--Device-notification-function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let supportDoNotDisturbModeCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("supportDoNotDisturbMode failed " + JSON.stringify(err));
  } else {
    console.info("supportDoNotDisturbMode success");
  }
}

Notification.supportDoNotDisturbMode(supportDoNotDisturbModeCallback);
```

<!--DelEnd-->


## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(): Promise<boolean>
```

Checks whether DND mode is supported. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSupportDoNotDisturbMode](arkts-notification-notificationmanager-issupportdonotdisturbmode-f-sys.md)()

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function supportDoNotDisturbMode(): Promise<boolean>--><!--Device-notification-function supportDoNotDisturbMode(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

Notification.supportDoNotDisturbMode().then((data: boolean) => {
  console.info("supportDoNotDisturbMode success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`supportDoNotDisturbMode failed, code is ${err}`);
});
```

<!--DelEnd-->
