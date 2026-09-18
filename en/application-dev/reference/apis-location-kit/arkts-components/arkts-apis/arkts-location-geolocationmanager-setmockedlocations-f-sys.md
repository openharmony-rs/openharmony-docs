# setMockedLocations (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## setMockedLocations

```TypeScript
function setMockedLocations(config: LocationMockConfig): void
```

Set the configuration parameters for location simulation.

**Since:** 9

**Required permissions:** 
- API version 20 and later: ohos.permission.MOCK_LOCATION
- API versions 9 to 19: N/A

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [LocationMockConfig](arkts-location-geolocationmanager-locationmockconfig-i-sys.md) | Yes | Indicates the configuration parameters for location simulation. Contains the array of locations and reporting intervals that need to be simulated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call &#36;{geoLocationManager.setMockedLocations} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let locations: Array<geoLocationManager.Location> = [
  {
    "latitude": 30.12,
    "longitude": 120.11,
    "altitude": 123,
    "accuracy": 1,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 1000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 31.13,
    "longitude": 121.11,
    "altitude": 123,
    "accuracy": 2,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 2000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 32.14,
    "longitude": 122.11,
    "altitude": 123,
    "accuracy": 3,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 3000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 33.15,
    "longitude": 123.11,
    "altitude": 123,
    "accuracy": 4,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 4000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 34.16,
    "longitude": 124.11,
    "altitude": 123,
    "accuracy": 5,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 5000000000,
    "additionSize": 0,
    "isFromMock": true
  }
];
let config: geoLocationManager.LocationMockConfig = { "timeInterval": 5, "locations": locations };
try {
  geoLocationManager.enableLocationMock();
  geoLocationManager.setMockedLocations(config);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
