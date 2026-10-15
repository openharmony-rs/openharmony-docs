# LocationAttributes (System API)

```TypeScript
export interface LocationAttributes
```

Location-based scenario attributes.

**Since:** 26.2.0

<!--Device-behaviorAwareness-export interface LocationAttributes--><!--Device-behaviorAwareness-export interface LocationAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## coordinates

```TypeScript
coordinates: Coordinates
```

Geographic coordinates.

**Type:** [Coordinates](arkts-multimodalawareness-behaviorawareness-coordinates-i-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocationAttributes-coordinates: Coordinates--><!--Device-LocationAttributes-coordinates: Coordinates-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## kind

```TypeScript
kind: 'location'
```

Discriminator field, fixed as 'location'.

**Type:** 'location'

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocationAttributes-kind: 'location'--><!--Device-LocationAttributes-kind: 'location'-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## locationName

```TypeScript
locationName?: string
```

Location name.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocationAttributes-locationName?: string--><!--Device-LocationAttributes-locationName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## locationType

```TypeScript
locationType?: LocationType
```

Location type.

**Type:** [LocationType](arkts-multimodalawareness-behaviorawareness-locationtype-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocationAttributes-locationType?: LocationType--><!--Device-LocationAttributes-locationType?: LocationType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
