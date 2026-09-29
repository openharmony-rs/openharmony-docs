# FusionFenceTransition (System API)

```TypeScript
export interface FusionFenceTransition
```

Indicates fusion fence transition information.

**Since:** 26.0.0

<!--Device-geoLocationManager-export interface FusionFenceTransition--><!--Device-geoLocationManager-export interface FusionFenceTransition-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## identifier

```TypeScript
identifier: string
```

Identifier of the fusion fence.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FusionFenceTransition-identifier: string--><!--Device-FusionFenceTransition-identifier: string-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## scene

```TypeScript
scene: FusionFenceScene
```

Indicates fusion fence scene.

**Type:** [FusionFenceScene](arkts-location-geolocationmanager-fusionfencescene-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FusionFenceTransition-scene: FusionFenceScene--><!--Device-FusionFenceTransition-scene: FusionFenceScene-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## transitionEvent

```TypeScript
transitionEvent: GeofenceTransitionEvent
```

Indicates the fence transition event.

**Type:** [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FusionFenceTransition-transitionEvent: GeofenceTransitionEvent--><!--Device-FusionFenceTransition-transitionEvent: GeofenceTransitionEvent-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.
