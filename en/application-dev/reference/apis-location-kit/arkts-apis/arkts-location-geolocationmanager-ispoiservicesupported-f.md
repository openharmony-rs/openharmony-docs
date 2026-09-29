# isPoiServiceSupported

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isPoiServiceSupported

```TypeScript
function isPoiServiceSupported(): boolean
```

Check whether the POI service is supported.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-geoLocationManager-function isPoiServiceSupported(): boolean--><!--Device-geoLocationManager-function isPoiServiceSupported(): boolean-End-->

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if POI service is available, returns `false` otherwise. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let poiServiceState = geoLocationManager.isPoiServiceSupported();
console.info("poiServiceState:" + poiServiceState);
```
