# @ohos.data.cloudData (Device-Cloud Service)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--Designer: @lvcong_oh-->
<!--Tester: @ltttjs; @logic42-->
<!--Adviser: @ge-yafang-->

The **cloudData** module provides the device-cloud strategy capability, enabling you to configure the device-cloud sync strategy.

 

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { cloudData } from '@kit.ArkData';
```

## StrategyType

Enumerates the types of the cloud-device sync strategy.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

| Name     | Value| Description       |
| --------- |---|-----------|
| NETWORK | 0 | Sync over the network.|

## NetWorkStrategy

Enumerates the network sync options.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

| Name     | Value| Description       |
| --------- |---|-----------|
| WIFI | 1 | Sync over Wi-Fi.|
| CELLULAR | 2 | Sync over the cellular network.  |

## AutoSyncTriggerMode

Enumerates the auto-sync trigger modes.

**Since:** 26.0.0

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

| Name| Value| Description|
|------|---|------|
| ACCOUNT_LOGIN | 0 | Triggered for account login.|
| CLOUD_SWITCH_ON | 1 | Triggered for sync switch.|
| NETWORK_RECOVER | 2 | Triggered after network recovery.|
| CLOUD_DATA_CHANGE | 3 | Triggered for cloud data changes.|
| USER_CHANGE | 4 | Triggered for user changes.|

## AutoSyncTriggerInfo

Defines the auto-sync trigger information.

**Since:** 26.0.0

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
|------|------|------|------|------|
| mode | [AutoSyncTriggerMode](#autosynctriggermode) | No| No| Auto-sync trigger mode.|

## cloudData.setCloudStrategy

setCloudStrategy(strategy: StrategyType, param?: Array&lt;commonType.ValueType&gt;): Promise&lt;void&gt;

Sets the cloud sync strategy of an application. This API uses a promise to return the result.
 
**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters**

| Name    | Type                                                                         | Mandatory| Description                            |
| ---------- |-----------------------------------------------------------------------------| ---- | -------------------------------- |
| strategy  | [StrategyType](#strategytype)                                               | Yes  | Type of the strategy to set.            |
| param | Array&lt;[commonType.ValueType](js-apis-data-commonType.md#valuetype)&gt; | No  | Strategy parameter. The type is **Array<commonType.ValueType>**. The actual input value is an enumerated value of [NetWorkStrategy](#networkstrategy), which can be **WIFI** or **CELLULAR**. By default, both Wi-Fi and cellular network strategies are supported.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported.|

**Example:**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Sync data over Wi-Fi only.
cloudData.setCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set cloud strategy. Code: ${err.code}, message: ${err.message}`);
});

```

## cloudData.onAutoSyncTrigger

onAutoSyncTrigger(observer: Callback&lt;AutoSyncTriggerInfo&gt;): void

Subscribes to an auto-sync trigger event when device-cloud sync is enabled and auto-sync is disabled for the application. When the auto-sync trigger condition is met, the callback is invoked.

**Since:** 26.0.0

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| observer | Callback&lt;[AutoSyncTriggerInfo](#autosynctriggerinfo)&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 801      | Capability not supported. |

**Example**

```ts
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);
```

## cloudData.offAutoSyncTrigger

offAutoSyncTrigger(observer?: Callback&lt;AutoSyncTriggerInfo&gt;): void

Unsubscribes from the auto-sync trigger event notification.

**Since:** 26.0.0

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| observer | Callback&lt;[AutoSyncTriggerInfo](#autosynctriggerinfo)&gt; | No| Callback to unsubscribe from. If an **observer** is passed, the specified callback is unsubscribed. If no **observer** is passed, all registered observers are unsubscribed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 801      | Capability not supported. |

**Example**

```ts
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

// Subscribe to an observer.
cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);

// Unsubscribe from a specified observer.
cloudData.offAutoSyncTrigger(autoSyncTriggerObserver);

// Unsubscribe from all observers.
cloudData.offAutoSyncTrigger();
```
 
