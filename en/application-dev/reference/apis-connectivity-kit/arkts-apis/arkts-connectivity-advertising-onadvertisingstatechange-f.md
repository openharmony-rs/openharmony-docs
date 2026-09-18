# onAdvertisingStateChange

## Modules to Import

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## onAdvertisingStateChange

```TypeScript
function onAdvertisingStateChange(callback: Callback<AdvertisingStateChangeInfo>): void
```

Subscribes to the NearLink advertising state change event. This API uses an asynchronous callback to return the result. When [advertising.startAdvertising](arkts-connectivity-advertising-startadvertising-f.md) is called to start advertising or [advertising.stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md) is called to stop advertising, the callback is triggered to return the corresponding advertising ID and advertising status. This API must be used in pairs with [advertising.offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md).

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md)&gt; | Yes | Callback used to return the advertising state change information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
