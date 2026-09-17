# requestEnableNotification

## Modules to Import

```TypeScript
```

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

Requests notification to be enabled for this application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

Requests notification to be enabled for this application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
