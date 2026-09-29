# cancelAll

## Modules to Import

```TypeScript
```

## cancelAll

```TypeScript
function cancelAll(callback: AsyncCallback<void>): void
```

Cancels all notifications. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancelAll](arkts-notification-notificationmanager-cancelall-f.md)

<!--Device-notification-function cancelAll(callback: AsyncCallback<void>): void--><!--Device-notification-function cancelAll(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


<a id="cancelall-1"></a>

## cancelAll

```TypeScript
function cancelAll(): Promise<void>
```

Cancels all notifications. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancelAll](arkts-notification-notificationmanager-cancelall-f.md)

<!--Device-notification-function cancelAll(): Promise<void>--><!--Device-notification-function cancelAll(): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
