# GeofenceTransition

```TypeScript
export interface GeofenceTransition
```

Geofence transition status.

**Since:** 12

<!--Device-geoLocationManager-export interface GeofenceTransition--><!--Device-geoLocationManager-export interface GeofenceTransition-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## beaconFence

```TypeScript
beaconFence?: BeaconFence
```

Indicate the beaconFence which transitionEvent occurs.

**Type:** [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md)

**Since:** 20

<!--Device-GeofenceTransition-beaconFence?: BeaconFence--><!--Device-GeofenceTransition-beaconFence?: BeaconFence-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## geofenceId

```TypeScript
geofenceId: number
```

ID of the geofence.

**Type:** number

**Since:** 12

<!--Device-GeofenceTransition-geofenceId: int--><!--Device-GeofenceTransition-geofenceId: int-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## transitionEvent

```TypeScript
transitionEvent: GeofenceTransitionEvent
```

Indicates the geofence transition status.

**Type:** [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md)

**Since:** 12

<!--Device-GeofenceTransition-transitionEvent: GeofenceTransitionEvent--><!--Device-GeofenceTransition-transitionEvent: GeofenceTransitionEvent-End-->

**System capability:** SystemCapability.Location.Location.Geofence
