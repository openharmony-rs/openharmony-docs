# getRangingCapability

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## getRangingCapability

```TypeScript
function getRangingCapability(): Promise<RangingCapabilitySupported>
```

Queries whether the current device supports ranging capability.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RangingCapabilitySupported](arkts-connectivity-ranging-rangingcapabilitysupported-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-ranging-service-disabled) | The ranging service is disabled. |
