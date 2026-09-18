# getDistanceBetweenLocations

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getDistanceBetweenLocations

```TypeScript
function getDistanceBetweenLocations(location1: Location, location2: Location): number
```

Obtains the distance between two locations.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location1 | [Location](arkts-location-geolocationmanager-location-i.md) | Yes | Indicates first location. |
| location2 | [Location](arkts-location-geolocationmanager-location-i.md) | Yes | Indicates second location. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the distance between two locations. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let location1: geoLocationManager.Location = {
    "latitude": 30.12,
    "longitude": 120.11,
    "altitude": 0,
    "accuracy": 0,
    "speed": 0,
    "timeStamp": 0,
    "direction": 0,
    "timeSinceBoot": 0,
    "additionSize": 0
  }
  let location2: geoLocationManager.Location = {
    "latitude": 30.12,
    "longitude": 120.11,
    "altitude": 0,
    "accuracy": 0,
    "speed": 0,
    "timeStamp": 0,
    "direction": 0,
    "timeSinceBoot": 0,
    "additionSize": 0
  }
  let distance = geoLocationManager.getDistanceBetweenLocations(location1, location2);
  console.info("distance:" + distance);
} catch (error) {
  console.error("getDistanceBetweenLocations: errCode" + error.code + ", errMessage" + error.message);
}
```
