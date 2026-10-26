# Coordinates (System API)

```TypeScript
export interface Coordinates
```

Geographic coordinates.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface Coordinates--><!--Device-behaviorAwareness-export interface Coordinates-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## latitude

```TypeScript
latitude: number
```

Latitude. Unit: degree. Value range: [-90,90].

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Coordinates-latitude: double--><!--Device-Coordinates-latitude: double-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## longitude

```TypeScript
longitude: number
```

Longitude. Unit: degree. Value range: [-180,180].

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Coordinates-longitude: double--><!--Device-Coordinates-longitude: double-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
