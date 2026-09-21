# on

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## on('locationChange')

```TypeScript
function on(type: 'locationChange', request: LocationRequest | ContinuousLocationRequest,
      callback: Callback<Location>): void
```

Subscribe location changed. You are advised to use the [onLocationChange](#onlocationchange) instead.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'locationChange' | Yes | Indicates the location service event to be subscribed to. |
| request | [LocationRequest](arkts-location-geolocationmanager-locationrequest-i.md) &#124; [ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md) | Yes | Indicates the location request parameters.<br>**Since:** 12 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('locationChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the geographical location.<br>**Applicable version:** 9 - 17 |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

// Method 1: Use LocationRequest as the input parameter.
let requestInfo: geoLocationManager.LocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'timeInterval': 1,
  'distanceInterval': 0,
  'maxAccuracy': 0
};
let locationChange = (location: geoLocationManager.Location): void => {
  console.info('locationChange: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.on('locationChange', requestInfo, locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// Method 2: Use ContinuousLocationRequest as the input parameter.
let request: geoLocationManager.ContinuousLocationRequest = {
  'interval': 1,
  'locationScenario': geoLocationManager.UserActivityScenario.NAVIGATION
};
let locationCallback = (location: geoLocationManager.Location): void => {
  console.info('locationCallback: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.on('locationChange', request, locationCallback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('locationError')

```TypeScript
function on(type: 'locationError', callback: Callback<LocationError>): void
```

Subscribe continuous location error changed.

**Since:** 12

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'locationError' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocationError](arkts-location-geolocationmanager-locationerror-e.md)&gt; | Yes | Indicates the callback for reporting the continuous location error. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('locationError')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let requestInfo: geoLocationManager.LocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'timeInterval': 1,
  'distanceInterval': 0,
  'maxAccuracy': 0
};
let locationChange = (location: geoLocationManager.Location): void => {
  console.info('locationChange: data: ' + JSON.stringify(location));
};
try {
  geoLocationManager.on('locationChange', requestInfo, locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

let locationErrorChange = (errcode: geoLocationManager.LocationError): void => {
  console.info('locationErrorChange: data: ' + JSON.stringify(errcode));
};
try {
  geoLocationManager.on('locationError', locationErrorChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('locationEnabledChange')

```TypeScript
function on(type: 'locationEnabledChange', callback: Callback<boolean>): void
```

Subscribe location switch changed.

**Since:** 9

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'locationEnabledChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the location switch status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('locationEnabledChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let locationEnabledChange = (state: boolean): void => {
    console.info('locationEnabledChange: ' + JSON.stringify(state));
}
try {
    geoLocationManager.on('locationEnabledChange', locationEnabledChange);
} catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('cachedGnssLocationsChange')

```TypeScript
function on(type: 'cachedGnssLocationsChange', request: CachedGnssLocationsRequest, 
      callback: Callback<Array<Location>>): void
```

Subscribe to cache GNSS locations update messages.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cachedGnssLocationsChange' | Yes | Indicates the location service event to be subscribed to. |
| request | [CachedGnssLocationsRequest](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md) | Yes | Indicates the cached GNSS locations request parameters. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt;&gt; | Yes | Indicates the callback for reporting the cached GNSS locations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('cachedGnssLocationsChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the geographical location.<br>**Applicable version:** 9 - 17 |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let cachedLocationsCb = (locations: Array<geoLocationManager.Location>): void => {
  console.info('cachedGnssLocationsChange: locations: ' + JSON.stringify(locations));
}
let requestInfo: geoLocationManager.CachedGnssLocationsRequest = {
  'reportingPeriodSec': 10,
  'wakeUpCacheQueueFull': true
};
try {
  geoLocationManager.on('cachedGnssLocationsChange', requestInfo, cachedLocationsCb);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('satelliteStatusChange')

```TypeScript
function on(type: 'satelliteStatusChange', callback: Callback<SatelliteStatusInfo>): void
```

Subscribe satellite status changed.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'satelliteStatusChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SatelliteStatusInfo](arkts-location-geolocationmanager-satellitestatusinfo-i.md)&gt; | Yes | Indicates the callback for reporting the satellite status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('satelliteStatusChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let gnssStatusCb = (satelliteStatusInfo: geoLocationManager.SatelliteStatusInfo): void => {
  console.info('satelliteStatusChange: ' + JSON.stringify(satelliteStatusInfo));
  // Number of satellites.
  let totalNumber: number = satelliteStatusInfo.satellitesNumber;
  let satelliteIds: Array<number> = satelliteStatusInfo.satelliteIds;
  let carrierToNoiseDensitys: Array<number> = satelliteStatusInfo.carrierToNoiseDensitys;
  let altitudes: Array<number> = satelliteStatusInfo.altitudes;
  let azimuths: Array<number> = satelliteStatusInfo.azimuths;
  let carrierFrequencies: Array<number> = satelliteStatusInfo.carrierFrequencies;
  let satelliteConstellations: Array<geoLocationManager.SatelliteConstellationCategory> | undefined = satelliteStatusInfo.satelliteConstellation;
  let satelliteAdditionalInfos: Array<number> | undefined = satelliteStatusInfo.satelliteAdditionalInfo;
  for (let i = 0;i < totalNumber; i++) {
    // Satellite ID.
    let satelliteId: number = satelliteIds[i];
    // Carrier-to-noise density ratio of the satellite whose ID is ${satelliteId}.
    let carrierToNoiseDensity: number = carrierToNoiseDensitys[i];
    // Altitude angle information of the satellite whose ID is ${satelliteId}.
    let altitude: number = altitudes[i];
    // Azimuth of the satellite whose ID is ${satelliteId}.
    let azimuth: number = azimuths[i];
    // Carrier frequency of the satellite whose ID is ${satelliteId}.
    let carrierFrequency: number = carrierFrequencies[i];
    if (satelliteConstellations != undefined) {
      // Constellation of the satellite whose ID is ${satelliteId}.
      let satelliteConstellation: geoLocationManager.SatelliteConstellationCategory = satelliteConstellations[i];
    }
    if (satelliteAdditionalInfos != undefined) {
      // Additional information about the satellite whose ID is ${satelliteId}, for example, use of the satellite in the latest location resolution and the availability of ephemeris data, almanac data, and carrier frequency information.
      let satelliteAdditionalInfo: number = satelliteAdditionalInfos[i];
    }
  }
}

try {
  geoLocationManager.on('satelliteStatusChange', gnssStatusCb);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('nmeaMessage')

```TypeScript
function on(type: 'nmeaMessage', callback: Callback<string>): void
```

Subscribe nmea message changed.

**Since:** 9

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'nmeaMessage' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Indicates the callback for reporting the nmea message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('nmeaMessage')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let nmeaCb = (str: string): void => {
  console.info('nmeaMessage: ' + JSON.stringify(str));
}

try {
  geoLocationManager.on('nmeaMessage', nmeaCb);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('gnssFenceStatusChange')

```TypeScript
function on(type: 'gnssFenceStatusChange', request: GeofenceRequest, want: WantAgent): void
```

Add a geofence and subscribe geofence status changed.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'gnssFenceStatusChange' | Yes | Indicates the location service event to be subscribed to. |
| request | [GeofenceRequest](arkts-location-geolocationmanager-geofencerequest-i.md) | Yes | Indicates the Geofence configuration parameters. |
| want | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | Yes | Indicates which ability to start when the geofence event is triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('gnssFenceStatusChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301600](../errorcode-geoLocationManager.md#3301600-geofence-operation-failed) | Failed to operate the geofence. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { wantAgent } from '@kit.AbilityKit';


let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      bundleName: "com.example.myapplication",
      abilityName: "EntryAbility",
      action: "action1"
    }
  ],
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj) => {
  let requestInfo: geoLocationManager.GeofenceRequest = {
    'scenario': 0x301,
    "geofence": { "latitude": 31.12, "longitude": 121.11, "radius": 100, "expiration": 10000 }
  };
  try {
    geoLocationManager.on('gnssFenceStatusChange', requestInfo, wantAgentObj);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
});
```


## on('countryCodeChange')

```TypeScript
function on(type: 'countryCodeChange', callback: Callback<CountryCode>): void
```

Registering the callback function for listening to country code changes.

**Since:** 9

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'countryCodeChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CountryCode](arkts-location-geolocationmanager-countrycode-i.md)&gt; | Yes | Indicates the callback for reporting country code changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('countryCodeChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301500](../errorcode-geoLocationManager.md#3301500-area-information-query-failed) | Failed to query the area information. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let callback = (code: geoLocationManager.CountryCode): void => {
  console.info('countryCodeChange: ' + JSON.stringify(code));
}

try {
  geoLocationManager.on('countryCodeChange', callback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


## on('bluetoothScanResultChange')

```TypeScript
function on(type: 'bluetoothScanResultChange', callback: Callback<BluetoothScanResult>): void
```

Registers and listens to bluetooth scanning results for location services.

**Since:** 16

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'bluetoothScanResultChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md)&gt; | Yes | Indicates the callback for reporting Bluetooth scan info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.on('bluetoothScanResultChange')} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';


let callback = (result: geoLocationManager.BluetoothScanResult): void => {
  console.info('bluetoothScanResultChange: ' + JSON.stringify(result));
};
try {
  geoLocationManager.on('bluetoothScanResultChange', callback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
