# startAdvertising

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## startAdvertising

```TypeScript
function startAdvertising(advertisingParams: AdvertisingParams): Promise<number>
```

Starts NearLink advertising. This API uses a promise to return the result. This API is applicable to scenarios where the local device capabilities or data needs to be advertised, such as device discovery and device information advertising. You can use [advertising.onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md) to monitor the advertising status. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-advertising-function startAdvertising(advertisingParams: AdvertisingParams): Promise<int>--><!--Device-advertising-function startAdvertising(advertisingParams: AdvertisingParams): Promise<int>-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| advertisingParams | [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md) | Yes | Advertising parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the advertising ID. The advertising ID is a unique ID randomly allocated. The value range is [0, 255]. Similar to [advertising.stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md) and [AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md).advertisingId, this ID can be used to distinguish the current advertising instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100040](../errorcode-nearlink-service.md#36100040-integer-out-of-range) | Integer out of range. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
