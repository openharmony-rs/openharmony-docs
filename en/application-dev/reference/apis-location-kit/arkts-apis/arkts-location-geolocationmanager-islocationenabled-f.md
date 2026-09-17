# isLocationEnabled

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isLocationEnabled

```TypeScript
function isLocationEnabled(): boolean
```

Obtain current location switch status.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the location switch on, returns `false` otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call &#36;{geoLocationManager.isLocationEnabled} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let locationEnabled = geoLocationManager.isLocationEnabled();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
