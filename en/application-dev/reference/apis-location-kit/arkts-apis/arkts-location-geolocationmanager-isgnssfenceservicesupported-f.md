# isGnssFenceServiceSupported

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isGnssFenceServiceSupported

```TypeScript
function isGnssFenceServiceSupported(): boolean
```

Check whether the GNSS fence service is supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-geoLocationManager-function isGnssFenceServiceSupported(): boolean--><!--Device-geoLocationManager-function isGnssFenceServiceSupported(): boolean-End-->

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if GNSS fence service is available, returns `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
