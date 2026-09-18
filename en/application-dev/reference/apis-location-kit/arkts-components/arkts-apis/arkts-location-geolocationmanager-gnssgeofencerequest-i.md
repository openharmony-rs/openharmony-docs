# GnssGeofenceRequest

Configuring parameters in GNSS geofence requests.

**Since:** 12

**System capability:** SystemCapability.Location.Location.Geofence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## fenceExtensionAbilityName

```TypeScript
fenceExtensionAbilityName?: string
```

Indicates the name of FenceExtensionAbility.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Location.Location.Geofence

## geofence

```TypeScript
geofence: Geofence
```

Circular fence information.

**Type:** [Geofence](arkts-location-geolocationmanager-geofence-i.md)

**Since:** 12

**System capability:** SystemCapability.Location.Location.Geofence

## geofenceTransitionCallback

```TypeScript
geofenceTransitionCallback: AsyncCallback<GeofenceTransition>
```

Indicates the callback for reporting the geofence transition status.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Location.Location.Geofence

## loiterTimeMs

```TypeScript
loiterTimeMs?: number
```

Indicates time for which a device is dwelling in the geofence, in milliseconds. If the device dwelling time reaches the value specified by this parameter, a GEOFENCE_TRANSITION_EVENT_DWELL event is reported. The value should be an integer.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.Location.Location.Geofence

## monitorTransitionEvents

```TypeScript
monitorTransitionEvents: Array<GeofenceTransitionEvent>
```

Indicates geofence transition status monitored.

**Type:** Array&lt;[GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Location.Location.Geofence

## notifications

```TypeScript
notifications?: Array<NotificationRequest>
```

Indicates the geofence notifications to publish.

**Type:** Array&lt;[NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Location.Location.Geofence
