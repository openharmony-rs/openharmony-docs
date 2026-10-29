# onAutoSyncTrigger

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## onAutoSyncTrigger

```TypeScript
function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void
```

Registers the auto sync trigger event notification when device-cloud sync is enabled and automatic sync is disabled for the application. When the auto trigger condition is met, the callback function is invoked.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-cloudData-function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void--><!--Device-cloudData-function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AutoSyncTriggerInfo](arkts-arkdata-clouddata-autosynctriggerinfo-i.md)&gt; | Yes | Callback invoked to return the auto sync trigger information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |

**Examples**

```TypeScript
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);
```
