# BeaconFenceRequest

Configuring parameters in BeaconFence request.

**Since:** 20

**System capability:** SystemCapability.Location.Location.Geofence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## beacon

```TypeScript
beacon: BeaconFence
```

Beacon fence information.

**Type:** [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Geofence

## fenceExtensionAbilityName

```TypeScript
fenceExtensionAbilityName?: string
```

Indicates the name of FenceExtensionAbility.

**Type:** string

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Geofence

## transitionCallback

```TypeScript
transitionCallback?: Callback<GeofenceTransition>
```

Indicates the callback for reporting the BeaconFence transition status.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md)&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Geofence
