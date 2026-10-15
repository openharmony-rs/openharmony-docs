# isDistributedEnabled

## Modules to Import

```TypeScript
```

<a id="isdistributedenabled1"></a>

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

Checks whether this device supports distributed notifications. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md)

<!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void--><!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |


<a id="isdistributedenabled2"></a>

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

Checks whether this device supports distributed notifications. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md)

<!--Device-notification-function isDistributedEnabled(): Promise<boolean>--><!--Device-notification-function isDistributedEnabled(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |
