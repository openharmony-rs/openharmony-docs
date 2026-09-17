# @ohos.data.cloudData (Device-Cloud Service)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @lvcong_oh-->
<!--Designer: @lvcong_oh-->
<!--Tester: @ltttjs; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d0710d1bb15ab1e8e3d2b0fba732dba4ba82539d translatedAt=2026-09-15T12:08:20.210Z pushedAt=2026-09-16T07:50:15.722Z -->

The Device-Cloud Service provides device-cloud strategy capabilities.

The device-cloud strategy provides the capability of configuring device-cloud synchronization policies.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { cloudData } from '@kit.ArkData';
```

## StrategyType

Enumerates the cloud sync strategy types.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

| Name      | Value | Description        |
| --------- |---|-----------|
| NETWORK | 0 | Synchronization over the network. |

## NetWorkStrategy

Enumerates the network policy parameters.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

| Name      | Value | Description        |
| --------- |---|-----------|
| WIFI | 1 | Wi-Fi network policy. |
| CELLULAR | 2 | Cellular network policy.   |

## AutoSyncTriggerMode

Enumerates the trigger modes of automatic synchronization.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
|------|---|------|
| ACCOUNT_LOGIN | 0 | Account login trigger mode. |
| CLOUD_SWITCH_ON | 1 | Sync switch trigger mode. |
| NETWORK_RECOVER | 2 | Trigger mode after network recovery. |
| CLOUD_DATA_CHANGE | 3 | Cloud data change trigger mode. |
| USER_CHANGE | 4 | User change trigger mode. |

## AutoSyncTriggerInfo

Defines the automatic synchronization trigger information.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
|------|------|------|------|------|
| mode | [AutoSyncTriggerMode](#autosynctriggermode) | No | No | Automatic synchronization trigger mode. |

## cloudData.setCloudStrategy

setCloudStrategy(strategy: StrategyType, param?: Array&lt;commonType.ValueType&gt;): Promise&lt;void&gt;

Sets the cloud sync strategy of the application itself. This API uses a promise to return the result.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters**

| Name | Type                                                                          | Mandatory | Description                             |
| -------------- |-----------------------------------------------------------------------------| --------- | --------------------------------------- |
| strategy  | [StrategyType](#strategytype)                                               | Yes   | Type of the strategy to configure.             |
| param | Array&lt;[commonType.ValueType](js-apis-data-commonType.md#valuetype)&gt; | No   | Strategy parameter, of the Array&lt;commonType.ValueType&gt; type. The actual value passed in is a [NetWorkStrategy](#networkstrategy) enum value, which can be WIFI or CELLULAR. By default, both the Wi-Fi and cellular network strategies are supported. |

**Returns**

| Type                | Description                      |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **ID** | **Error Message**                                                 |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Sync over WIFI only.
cloudData.setCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set cloud strategy. Code: ${err.code}, message: ${err.message}`);
});

```

## cloudData.onAutoSyncTrigger

onAutoSyncTrigger(observer: Callback&lt;AutoSyncTriggerInfo&gt;): void

Registers the auto sync trigger event notification when device-cloud sync is enabled and automatic sync is disabled for the application. When the auto trigger condition is met, the callback function is invoked.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
|--------|------|------|------|
| observer | Callback&lt;[AutoSyncTriggerInfo](#autosynctriggerinfo)&gt; | Yes | Callback invoked to return the auto sync trigger information. |

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                             |
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

Unsubscribes from the auto sync trigger event notification.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
|--------|------|------|------|
| observer | Callback&lt;[AutoSyncTriggerInfo](#autosynctriggerinfo)&gt; | No | Callback for the auto sync trigger event. If observer is passed in, the subscription of the specified callback is canceled; if observer is not passed in, all registered subscriptions are canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                             |
| -------- | ---------------------------------------------------- |
| 801      | Capability not supported. |

**Example**

```ts
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
<!--no_check-->
