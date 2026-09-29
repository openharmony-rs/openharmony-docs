# isBeaconFenceSupported

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isBeaconFenceSupported

```TypeScript
function isBeaconFenceSupported(): boolean
```

Check whether the BeaconFence service is supported.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-geoLocationManager-function isBeaconFenceSupported(): boolean--><!--Device-geoLocationManager-function isBeaconFenceSupported(): boolean-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if BeaconFence service is available, returns `false` otherwise. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isBeaconFenceSupported = geoLocationManager.isBeaconFenceSupported();
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
