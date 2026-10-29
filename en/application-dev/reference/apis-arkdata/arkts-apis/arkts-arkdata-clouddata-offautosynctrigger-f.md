# offAutoSyncTrigger

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## offAutoSyncTrigger

```TypeScript
function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void
```

Unsubscribes from the auto sync trigger event notification.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-cloudData-function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void--><!--Device-cloudData-function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AutoSyncTriggerInfo](arkts-arkdata-clouddata-autosynctriggerinfo-i.md)&gt; | No | Callback for the auto sync trigger event. If observer is passed in, the subscription of the specified callback is canceled; if observer is not passed in, all registered subscriptions are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

// Subscribe.
cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);

// Cancel the specified subscription.
cloudData.offAutoSyncTrigger(autoSyncTriggerObserver);

// Cancel all subscriptions.
cloudData.offAutoSyncTrigger();
```
