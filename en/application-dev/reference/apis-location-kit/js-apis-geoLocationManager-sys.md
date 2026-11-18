# @ohos.geoLocationManager (Geolocation Manager) (System API)
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @liu-binjun-->
<!--Designer: @liu-binjun-->
<!--Tester: @mhy123456789-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=018cf6704825ff3d82842e6150ca59994fa23d90 translatedAt=2026-11-03T04:39:24.908Z pushedAt=2026-11-03T12:08:25.502Z nl=1 -->

The **geoLocationManager** module provides location services such as Global Navigation Satellite System (GNSS)-based positioning, network positioning, geofencing, as well as geocoding and reverse geocoding.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.geoLocationManager (Geolocation Manager)](js-apis-geoLocationManager.md).
> This module supports only the WGS-84 coordinate system.

## Applying for Permissions

Before using basic location capabilities, check whether your application has been granted the permission to access the device location information. If not, your application needs to obtain the permission from the user as described below.

The system provides the following location permissions:
- ohos.permission.LOCATION

- ohos.permission.APPROXIMATELY_LOCATION

- ohos.permission.LOCATION_IN_BACKGROUND

If your application needs to access the device location information, it must first apply for required permissions. Specifically speaking:

API versions earlier than 9: Apply for **ohos.permission.LOCATION**.

API version 9 and later: Apply for **ohos.permission.APPROXIMATELY\_LOCATION**, or apply for **ohos.permission.APPROXIMATELY\_LOCATION** and **ohos.permission.LOCATION**. Note that **ohos.permission.LOCATION** cannot be applied for separately.

| API Version| Location Permission| Permission Application Result| Location Accuracy|
| -------- | -------- | -------- | -------- |
| Earlier than 9| ohos.permission.LOCATION | Success| Location accurate to meters|
| 9 and later| ohos.permission.LOCATION | Failure| No location obtained|
| 9 and later| ohos.permission.APPROXIMATELY_LOCATION | Success| Location accurate to 5 kilometers|
| 9 and later| ohos.permission.APPROXIMATELY_LOCATION and ohos.permission.LOCATION| Success| Location accurate to meters|

To access the device location information when running in the background, an application needs to request for a continuous task of the LOCATION type. In this way, the system continues to report device location information after your application moves to the background. For details about how to request for a continuous task, see [Continuous Task](../../task-management/continuous-task.md).

A user can grant the **ohos.permission.LOCATION_IN_BACKGROUND** permission for an application on the setting page. For details, see [ohos.permission.LOCATION_IN_BACKGROUND](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation_in_background).

You can declare the required permission in your application's configuration file. For details, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).


## Modules to Import

```ts
import { geoLocationManager } from '@kit.LocationKit';
```

## GeoAddress

Geocoding address information.

**System capability**: SystemCapability.Location.Location.Geocoder

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| isFromMock | Boolean | No| Yes| **true**: The geographic address is obtained from the mock reverse geocoding function.<br>**false**: The geographic address is not obtained from the mock reverse geocoding function.<br>**System API**: This is a system API.|


## GeofenceTransitionEvent<sup>12+</sup>

Geofence transition event.

**System capability:** SystemCapability.Location.Location.Geofence

| Name | Value | Description |
| -------- | -------- | -------- |
| GEOFENCE_TRANSITION_EVENT_APPROACHING_GEOFENCE    | 8 | This event indicates that the device is approaching a geofence area.<br/>**System API**: This API is a system API. |
| GEOFENCE_TRANSITION_EVENT_LEAVING_GEOFENCE    | 16 | This event indicates that the device has left a geofence area.<br/>**System API**: This API is a system API. |
| GEOFENCE_TRANSITION_EVENT_NEAR_WANDER    | 32 | This event indicates that the device is approaching a geofence area and has been wandering for more than 15 minutes.<br/>**System API**: This API is a system API. |


## FusionFenceRequestParams

Defines the fused fence request information.

**Since:** 26.0.0

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction**: This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| identifier | string | No | No | Indicates the unique identifier of the fused fence.<br/>**System API**: This is a system API. |
| scene | FusionFenceScene&lt;[FusionFenceScene](#fusionfencescene)&gt; | No | No | Indicates the fused fence scene.<br/>**System API**: This is a system API. |
| fenceType | number | No | No | Indicates the fused fence type. For details, see FusionFenceType&lt;[FusionFenceType](#fusionfencetype)&gt;. Set the value by binary bit. For example, 3 (binary 11) indicates both the GNSS fence and the CELLULAR fence.<br/>**System API**: This is a system API. |
| poiType | string | No | Yes | Indicates the POI type.<br/>**System API**: This is a system API. |
| poiLocation | Point&lt;[Point](#point)&gt; | No | No | Indicates the POI location information.<br/>**System API**: This is a system API. |
| monitorTransitionEvents | number | No | No | Indicates the fence events to monitor. For details, see GeofenceTransitionEvent&lt;[GeofenceTransitionEvent](#geofencetransitionevent12)&gt;. Set the value by binary bit. For example, 3 (binary 11) indicates monitoring both the fence entering and fence leaving events.<br/>**System API**: This is a system API. |
| loiterTimeMs | number | No | No | Indicates the loitering time. The unit is milliseconds. The value range is greater than 0. If the loitering event is monitored, the loitering event is reported when the time the device loiters in the fence reaches this value.<br/>**System API**: This is a system API. |
| gnssFences | Array&lt;[GnssFence](#gnssfence)&gt; | No | Yes | Indicates the GNSS fence information set. If GNSS is selected in FusionFenceType&lt;[FusionFenceType](#fusionfencetype)&gt;, this parameter is mandatory.<br/>**System API**: This is a system API. |
| cellFences | Array&lt;[CellFence](#cellfence)&gt; | No | Yes | Indicates the CELL fence information set. If CELLULAR is selected in FusionFenceType&lt;[FusionFenceType](#fusionfencetype)&gt;, this parameter is mandatory.<br/>**System API**: This is a system API. |
| wifiFences | Array&lt;[WifiFence](#wififence)&gt; | No | Yes | Indicates the Wi-Fi fence information set. If WIFI is selected in FusionFenceType&lt;[FusionFenceType](#fusionfencetype)&gt;, this parameter is mandatory.<br/>**System API**: This is a system API. |
| expirationMs | number | No | No | Indicates the fence lifetime. The unit is milliseconds. The value range is greater than 0.<br/>**System API**: This is a system API. |
| fenceTransitionCallback | Callback&lt;[FusionFenceTransition](#fusionfencetransition)&gt; | No | No | Indicates the callback function used to receive fence events.<br/>**System API**: This is a system API. |


## FusionFenceScene

Fused fence scene.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| AIRPORT    | 1 | Indicates the airport scene.<br/>**System API**: This is a system API. |
| TRAIN_STATION    | 2 | Indicates the train station scene.<br/>**System API**: This is a system API. |
| SUBWAY    | 3 | Indicates the subway scene.<br/>**System API**: This is a system API. |
| SHOP    | 4 | Indicates the shopping mall scene.<br/>**System API**: This is a system API. |


## FusionFenceType

The fused fence type uses binary flags. When this type is used, the bit corresponding to each supported fence type is set to 1. For example, if GNSS and CELLULAR fences are supported, the value is 0011 (binary), which is 3 in decimal; if all four fence types are supported, the value is 1111 (binary), which is 15 in decimal.

**Since:** 26.0.0

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction**: This API is only available under the Stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| GNSS    | 1 | The lowest bit of the four-bit binary number, indicating a GNSS fence.<br/>**System API**: This API is a system API. |
| CELLULAR    | 2 | The second bit from low to high of the four-bit binary number, indicating a CELLULAR fence.<br/>**System API**: This API is a system API. |
| WIFI    | 4 | The third bit from low to high of the four-bit binary number, indicating a Wi-Fi fence.<br/>**System API**: This API is a system API. |
| BLUETOOTH    | 8 | The highest bit of the four-bit binary number, indicating a Bluetooth fence.<br/>**System API**: This API is a system API. |


## Point

POI location information.

**Since:** 26.0.0

**System capability**: SystemCapability.Location.Location.Core

**Model restriction**: This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| latitude | number | No | No | Indicates the latitude. The value range is -90 to 90. |
| longitude | number | No | No | Indicates the longitude. The value range is -180 to 180. |


## GnssFence

GNSS fence information.

**Since:** 26.0.0

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction**: This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| gnssFenceType | number | No | No | Indicates the GNSS fence type. For details, see GnssFenceType&lt;[GnssFenceType](#gnssfencetype)&gt;. Multiple GNSS fence types are supported. For example, 3 indicates that both circular and polygon fences are included.<br/>**System API**: This API is a system API. |
| circularFence | Geofence&lt;[Geofence](js-apis-geoLocationManager.md#geofence)&gt; | No | Yes | Indicates the set of circular fence information. If CIRCULAR is selected in GnssFenceType&lt;[GnssFenceType](#gnssfencetype)&gt;, this parameter is mandatory.<br/>**System API**: This API is a system API. |
| polygon | Array&lt;[Point](#point)&gt; | No | Yes | Indicates the set of polygon fence information. If POLYGON is selected in GnssFenceType&lt;[GnssFenceType](#gnssfencetype)&gt;, this parameter is mandatory.<br/>**System API**: This API is a system API. |


## GnssFenceType

Enumerates the GNSS fence types.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| POLYGON    | 1 | Indicates a polygon fence.<br/>**System API**: This API is a system API. |
| CIRCULAR    | 2 | Indicates a circular fence.<br/>**System API**: This API is a system API. |


## CellFence

CELL fence information.

**Since:** 26.0.0

**System capability**: SystemCapability.Location.Location.Geofence

**Model restriction**: This API is only available under the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| cellInfos | Array&lt;[CellInfo](#cellinfo23)&gt; | No | No | Indicates the CELL fence information set.<br/>**System API**: This API is a system API. |


## WifiFence

Wi-Fi fence information.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| type | WifiFingerprintType&lt;[WifiFingerprintType](#wififingerprinttype)&gt; | No | No | Indicates the Wi-Fi fingerprint algorithm type.<br/>**System API**: This is a system API. |
| wifiFeatures | Array&lt;[WirelessSignalFeature](#wirelesssignalfeature)&gt; | No | No | Indicates the Wi-Fi fingerprint information set.<br/>**System API**: This is a system API. |


## WifiFingerprintType

Wi-Fi fingerprint algorithm type.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| SEMANTIC    | 1 | Indicates the semantic algorithm.<br/>**System API**: This API is a system API. |
| LOCATION    | 2 | Indicates the high-precision fingerprint algorithm.<br/>**System API**: This API is a system API. |


## WirelessSignalFeature

Wi-Fi fingerprint information.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| rssiAvg | number | No | No | Indicates the average RSSI.<br/>**System API**: This is a system API. |
| rssiStandardDeviation | number | No | No | Indicates the standard deviation of RSSI.<br/>**System API**: This is a system API. |
| mac | Array&lt;string&gt; | No | No | Indicates the set of device MAC address information.<br/>**System API**: This is a system API. |


## FusionFenceTransition

Fused fence callback event information.

**Since:** 26.0.0

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the Stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| identifier | string | No | No | Indicates the unique identifier of the fused fence.<br/>**System API**: This is a system API. |
| scene | FusionFenceScene&lt;[FusionFenceScene](#fusionfencescene)&gt; | No | No | Indicates the fused fence scene.<br/>**System API**: This is a system API. |
| transitionEvent | GeofenceTransitionEvent&lt;[GeofenceTransitionEvent](#geofencetransitionevent12)&gt; | No | No | Indicates the fence event.<br/>**System API**: This is a system API. |

## ReverseGeocodingMockInfo

Defines the configuration of the mock reverse geocoding function.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| location |  [ReverseGeoCodeRequest](js-apis-geoLocationManager.md#reversegeocoderequest) | No| No| Latitude and longitude information.<br>**System API**: This is a system API.|
| geoAddress |  [GeoAddress](#geoaddress) | No| No|Geographical name.<br>**System API**: This is a system API.|


## LocationMockConfig

Defines the configuration of the mock location switch.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| timeInterval | number | No| No| Time interval at which mock locations are reported, in seconds.<br>**System API**: This is a system API.|
| locations | Array&lt;[Location](js-apis-geoLocationManager.md#location)&gt; | No | No | Indicates the array of simulated locations. <br>**System API:** This API is a system API.|

## LocatingRequiredDataConfig<sup>10+</sup>

Defines the configuration for obtaining the required data of the location service.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| type | [LocatingRequiredDataType](#locatingrequireddatatype10) | No| No| Type of the required data.<br>**System API**: This is a system API.|
| needStartScan |  boolean | No| No| **true**: Scanning needs to be initiated.<br>**false**: Scanning does not need to be initiated.<br>**System API**: This is a system API.|
| scanInterval |  number | No| Yes| Scanning interval, in milliseconds. The specified value must be greater than **0**. The default value is **10000**.<br>**System API**: This is a system API.|
| scanTimeout |  number | No| Yes| Scanning timeout interval, in milliseconds. The value ranges from **0** to **600000**. The default value is **10000**.<br>**System API**: This is a system API.|
| slotId<sup>23+</sup> |  number | No| Yes| Slot ID of a SIM card.<br>**0**: slot 1.<br>**1**: slot 2.<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|
| arfcn<sup>23+</sup> |  Array&lt;number&gt; | No| Yes| Absolute Radio Frequency Channel Number (ARFCN).<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|
| plmnId<sup>23+</sup> |  Array&lt;number&gt; | No| Yes| Public Land Mobile Network Identifier (PLMN ID) of a SIM card.<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|


## LocatingRequiredData<sup>10+</sup>

Defines the required data of the location service, including the Wi-Fi or Bluetooth scanning result. After obtaining the data, an application can use the data for services such as network positioning.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| wifiData | [WifiScanInfo](#wifiscaninfo10) | No| Yes| Wi-Fi scanning result.<br>**System API**: This is a system API.|
| bluetoothData |  [BluetoothScanInfo](#bluetoothscaninfo10) | No| Yes| Bluetooth scanning result.<br>**System API**: This is a system API.|
| slotId<sup>23+</sup> |  number | No| Yes| Slot ID of a SIM card.<br>**0**: slot 1.<br>**1**: slot 2.<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|
| campedCellInfo<sup>23+</sup> |  [CellInfo](#cellinfo23)| No | Yes | Indicates the camped cell information.<br> **System API**: This API is a system API.<br>**Model restriction:** This API is only available under the Stage model.|
| neighboringCellInfo<sup>23+</sup> |  Array&lt;[CellInfo](#cellinfo23)&gt; | No | Yes | Indicates the neighboring cell information.<br> **System API**: This API is a system API.<br>**Model restriction:** This API is only available under the Stage model.|


## WifiScanInfo<sup>10+</sup>

Defines the Wi-Fi scanning information, including the SSID, BSSID, and RSSI of the scanned Wi-Fi hotspot.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ssid | string | No| No| Service set identifier (SSID) of a Wi-Fi hotspot, in UTF-8 format.<br>**System API**: This is a system API.|
| bssid | string | No| No| Base station subsystem identifier (BSSID) of a Wi-Fi hotspot.<br> **System API**: This is a system API.|
| rssi | number | No| No| Received signal strength indicator (RSSI) of a Wi-Fi hotspot, in dBm.<br> **System API**: This is a system API.|
| frequency | number | No| No| Frequency of a Wi-Fi hotspot, in Hz.<br>**System API**: This is a system API.|
| timestamp | number | No| No| Timestamp, in microseconds.<br> **System API**: This is a system API.|


## BluetoothScanInfo<sup>10+</sup>

Defines the Bluetooth scanning information.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| deviceName | string | No| No| Name of a Bluetooth device.<br> **System API**: This is a system API.|
| macAddress | string | No| No| MAC address of a Bluetooth device.<br> **System API**: This is a system API.|
| rssi | number | No| No| Signal strength of a Bluetooth device, in dBm.<br> **System API**: This is a system API.|
| timestamp | number | No| No| Timestamp, in microseconds.<br> **System API**: This is a system API.|


## CellInfo<sup>23+</sup>

Defines cellular cell information.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| timeSinceBoot | number | No| No| Duration from the time when the device is started to the time when the location is successfully obtained, in nanoseconds. Enabling and then disabling the airplane mode is not considered as a device restart.<br>**System API**: This is a system API.|
| cellId | number | No| No| Cellular cell ID.<br> **System API**: This is a system API.|
| lac | number | No| No| Location area code.<br>**System API**: This is a system API.|
| mcc | number | No| No| Mobile country code (MCC).<br>**System API**: This is a system API.|
| mnc | number | No| No| Mobile network code (MNC).<br> **System API**: This is a system API.|
| rat | number | No| No| Radio access technology.<br> **System API**: This is a system API.|
| signalIntensity | number | No| No| Signal strength.<br>**System API**: This is a system API.|
| arfcn | number | No| No| Absolute Radio Frequency Channel Number (ARFCN).<br> **System API**: This is a system API.|
| pci | number | No| No| Physical cell ID.<br>**System API**: This is a system API.|
| tac | number | No | Yes | Indicates the tracking area code. <br>**System API**: This API is a system API.<br />**Since:** 26.0.0 <br />**Model restriction:** This API is only available under the Stage model.|
| additionsMap | Map&lt;string, string&gt; | No | Yes | Additional information. <br>**System API**: This API is a system API.|


## LocationPrivacyType

Defines the privacy statement type.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Value| Description|
| -------- | -------- | -------- |
| OTHERS | 0 | Other scenarios. Reserved field.<br>**System API**: This is a system API.|
| STARTUP | 1 | Privacy statement displayed in the startup wizard. The user needs to choose whether to agree with the statement.<br> **System API**: This is a system API.|
| CORE_LOCATION | 2 | Privacy statement displayed when enabling the location service.<br> **System API**: This is a system API.|

## LocatingRequiredDataType<sup>10+</sup>

Defines the type of the required data of the location service.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Value| Description|
| -------- | -------- | -------- |
| WIFI  | 1 | Wi-Fi scanning information.<br> **System API**: This is a system API.|
| BLUETOOTH | 2 | Bluetooth scanning information.<br> **System API**: This is a system API.|
| CELLULAR<sup>23+</sup> | 3 | Cellular cell information.<br> **System API**: This is a system API.|


## LocationIconStatus<sup>12+</sup>

Defines the location icon status.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

| Name| Value| Description|
| -------- | -------- | -------- |
| LOCATING_NOT_STARTED  | 0 | No location services are available and the location icon does not need to be displayed.<br> **System API**: This is a system API.|
| LOCATING_STARTED | 1 | Common location is in progress, and the common location icon needs to be displayed.<br> **System API**: This is a system API.|
| HD_LOCATING_STARTED | 2 | High-precision location is in progress, and the high-precision location icon needs to be displayed.<br> **System API**: This is a system API.|


## geoLocationManager.on('locatingRequiredDataChange')<sup>10+</sup>

on(type: 'locatingRequiredDataChange', config: LocatingRequiredDataConfig, callback: Callback&lt;Array&lt;LocatingRequiredData&gt;&gt;): void

Subscribes to changes in the required data of the location service, including Wi-Fi and Bluetooth scanning information. An application can then determine whether to enable Wi-Fi and Bluetooth scanning based on the return result. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type. The value **locatingRequiredDataChange** indicates a change in the required data of the location service.|
  | config | [LocatingRequiredDataConfig](#locatingrequireddataconfig10) | Yes| Configuration for obtaining the required data of the location service.|
  | callback | Callback&lt;Array&lt;[LocatingRequiredData](#locatingrequireddata10)&gt;&gt; | Yes| Callback used to return the data required by the location service.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.on('locatingRequiredDataChange')} due to limited device capabilities.          |
|3301800 | Failed to start WiFi or Bluetooth scanning.                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  let callback = (code: Array<geoLocationManager.LocatingRequiredData>): void => {
    console.info('locatingRequiredDataChange: ' + JSON.stringify(code));
  }
  let config: geoLocationManager.LocatingRequiredDataConfig = { 'type': 1, 'needStartScan': true, 'scanInterval': 10000 };
  try {
    geoLocationManager.on('locatingRequiredDataChange', config, callback);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.off('locatingRequiredDataChange')<sup>10+</sup>

off(type: 'locatingRequiredDataChange', callback?: Callback&lt;Array&lt;LocatingRequiredData&gt;&gt;): void

Unsubscribes from changes in the required data of the location service and stops Wi-Fi and Bluetooth scanning.

**Required permissions**: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type. The value **locatingRequiredDataChange** indicates a change in the required data of the location service.|
  | callback | Callback&lt;Array&lt;[LocatingRequiredData](#locatingrequireddata10)&gt;&gt; | No| Callback to unregister. The callback must be the same as that passed by the **on** API. If this parameter is not specified, all callbacks of the specified event type are unregistered.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.off('locatingRequiredDataChange')} due to limited device capabilities.          |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  let callback = (code: Array<geoLocationManager.LocatingRequiredData>): void => {
    console.info('locatingRequiredDataChange: ' + JSON.stringify(code));
  }
  let config: geoLocationManager.LocatingRequiredDataConfig = { 'type': 1, 'needStartScan': true, 'scanInterval': 10000 };
  try {
    geoLocationManager.on('locatingRequiredDataChange', config, callback);
    geoLocationManager.off('locatingRequiredDataChange', callback);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```

## geoLocationManager.enableLocation

enableLocation(callback: AsyncCallback&lt;void&gt;): void

Enables the location service. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the location service is successfully enabled, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.enableLocation} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                              |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.enableLocation((err) => {
      if (err) {
        console.error('enableLocation: err=' + JSON.stringify(err));
      }
    });
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.enableLocation

enableLocation(): Promise&lt;void&gt;

Enables the location service. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**System capability**: SystemCapability.Location.Location.Core

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.enableLocation} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    geoLocationManager.enableLocation().then(() => {
      console.info('promise, enableLocation succeed');
    })
      .catch((error: BusinessError) => {
        console.error('promise, enableLocation: error=' + JSON.stringify(error));
      });
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```

## geoLocationManager.disableLocation

disableLocation(): void

Disables the location service.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**System capability**: SystemCapability.Location.Location.Core

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.disableLocation} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.disableLocation();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```

## geoLocationManager.enableLocationMock

enableLocationMock(): void

Enables the mock location switch.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.enableLocationMock} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |
|3301100 | The location switch is off.|

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.enableLocationMock();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.disableLocationMock

disableLocationMock(): void

Disables the mock location switch.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.disableLocationMock} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |
|3301100 | The location switch is off.|

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.disableLocationMock();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.setMockedLocations

setMockedLocations(config: LocationMockConfig): void

Sets the mock location information. The mock locations will be reported at the interval specified in this API.

This API can be invoked only after [geoLocationManager.enableLocationMock](#geolocationmanagerenablelocationmock) is called.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config |  [LocationMockConfig](#locationmockconfig) | Yes| Mock location information, including the interval for reporting the mock locations and the array of the mock locations.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.setMockedLocations} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |
|3301100 | The location switch is off.|

**Example**

  ```ts
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


## geoLocationManager.enableReverseGeocodingMock

enableReverseGeocodingMock(): void

Enables the mock reverse geocoding function.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.enableReverseGeocodingMock} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.enableReverseGeocodingMock();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.disableReverseGeocodingMock

disableReverseGeocodingMock(): void

Disables the mock geocoding function.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.disableReverseGeocodingMock} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.disableReverseGeocodingMock();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.setReverseGeocodingMockInfo

setReverseGeocodingMockInfo(mockInfos: Array&lt;ReverseGeocodingMockInfo&gt;): void

Sets information of the mock reverse geocoding function, including the mapping between a location and geographical name. If the location is contained in the configurations during reverse geocoding query, the corresponding geographical name will be returned.

This API can be invoked only after [geoLocationManager.enableReverseGeocodingMock](#geolocationmanagerenablereversegeocodingmock) is called.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOCK_LOCATION

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | mockInfos | Array&lt;[ReverseGeocodingMockInfo](#reversegeocodingmockinfo)&gt; | Yes| Array of information of the mock reverse geocoding function, including a location and a geographical name.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.<br/>Applicable versions: 20+                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.setReverseGeocodingMockInfo} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  let mockInfos: Array<geoLocationManager.ReverseGeocodingMockInfo> = [
    {
      "location": {
        "locale": "zh",
        "latitude": 30.12,
        "longitude": 120.11,
        "maxItems": 1
      },
      "geoAddress": {
        "locale": "zh",
        "latitude": 30.12,
        "longitude": 120.11,
        "isFromMock": true
      }
    },
    {
      "location": {
        "locale": "zh",
        "latitude": 31.12,
        "longitude": 121.11,
        "maxItems": 1
      },
      "geoAddress": {
        "locale": "zh",
        "latitude": 31.12,
        "longitude": 121.11,
        "isFromMock": true
      }
    },
    {
      "location": {
        "locale": "zh",
        "latitude": 32.12,
        "longitude": 122.11,
        "maxItems": 1
      },
      "geoAddress": {
        "locale": "zh",
        "latitude": 32.12,
        "longitude": 122.11,
        "isFromMock": true
      }
    },
    {
      "location": {
        "locale": "zh",
        "latitude": 33.12,
        "longitude": 123.11,
        "maxItems": 1
      },
      "geoAddress": {
        "locale": "zh",
        "latitude": 33.12,
        "longitude": 123.11,
        "isFromMock": true
      }
    },
    {
      "location": {
        "locale": "zh",
        "latitude": 34.12,
        "longitude": 124.11,
        "maxItems": 1
      },
      "geoAddress": {
        "locale": "zh",
        "latitude": 34.12,
        "longitude": 124.11,
        "isFromMock": true
      }
    },
  ];
  try {
    geoLocationManager.enableReverseGeocodingMock();
    geoLocationManager.setReverseGeocodingMockInfo(mockInfos);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.isLocationPrivacyConfirmed

isLocationPrivacyConfirmed(type: LocationPrivacyType): boolean

Queries whether the user agrees to the location service privacy statement and whether to enable the location service. Only system applications can call this API.

**System API**: This is a system API.

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type |  [LocationPrivacyType](#locationprivacytype)| Yes | Specifies the privacy statement scenario, for example, the privacy statement in the startup wizard, the privacy statement displayed when enabling the network location function, etc. |

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | true: The user agrees to the location service privacy statement.<br/>false: The user does not agree to the location service privacy statement. |

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.isLocationPrivacyConfirmed} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    let isConfirmed = geoLocationManager.isLocationPrivacyConfirmed(1);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.setLocationPrivacyConfirmStatus

setLocationPrivacyConfirmStatus(type: LocationPrivacyType, isConfirmed: boolean): void

Sets the status of the user's selection of the location service privacy statement and records whether the user agrees to enable the location service. Only system applications can call this API.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | [LocationPrivacyType](#locationprivacytype) | Yes | Specifies the privacy statement scenario, for example, the privacy statement in the startup wizard and the privacy statement displayed when the network location function is enabled. |
  | isConfirmed | boolean | Yes | true: the user agrees to the location service privacy statement.<br/>false: the user disagrees with the location service privacy statement. |

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.setLocationPrivacyConfirmStatus} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    geoLocationManager.setLocationPrivacyConfirmStatus(1, true);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.getLocatingRequiredData<sup>10+</sup>

getLocatingRequiredData(config: LocatingRequiredDataConfig): Promise&lt;Array&lt;LocatingRequiredData&gt;&gt;

Obtains the required data of the location service. This API uses a promise to return the result.

**Required permissions**: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | config | [LocatingRequiredDataConfig](#locatingrequireddataconfig10) | Yes| Configuration for obtaining the required data of the location service.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;Array&lt;[LocatingRequiredData](#locatingrequireddata10)&gt;&gt; | Promise used to return the required data for the location service, such as the Wi-Fi and Bluetooth scanning information.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.getLocatingRequiredData} due to limited device capabilities.          |
|3301800  | Failed to start WiFi or Bluetooth scanning.                    |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let config: geoLocationManager.LocatingRequiredDataConfig = { 'type': 1, 'needStartScan': true, 'scanInterval': 10000 };
  try {
    geoLocationManager.getLocatingRequiredData(config).then((result) => {
      console.info('getLocatingRequiredData return: ' + JSON.stringify(result));
    })
      .catch((error: BusinessError) => {
        console.error('promise, getLocatingRequiredData: error=' + JSON.stringify(error));
      });
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.on('locationIconStatusChange')<sup>12+</sup>

on(type: 'locationIconStatusChange', callback: Callback&lt;LocationIconStatus&gt;): void

Subscribes to status changes of the location icon. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type. Event type. The value **locationIconStatusChange** indicates status changes of the location icon.|
  | callback | Callback&lt;[LocationIconStatus](#locationiconstatus12)&gt; | Yes| Callback used to return the location icon status.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.on('locationIconStatusChange')} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                        |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  let callback = (code: geoLocationManager.LocationIconStatus): void => {
    console.info('LocationIconStatus: ' + JSON.stringify(code));
  }
  try {
    geoLocationManager.on('locationIconStatusChange', callback);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.off('locationIconStatusChange')<sup>12+</sup>

off(type: 'locationIconStatusChange', callback?: Callback&lt;LocationIconStatus&gt;): void

Unsubscribes from status changes of the location icon.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Event type. Event type. The value **locationIconStatusChange** indicates status changes of the location icon.|
  | callback | Callback&lt;[LocationIconStatus](#locationiconstatus12)&gt;  | No| Callback to unregister. The callback must be the same as that passed by the **on** API. If this parameter is not specified, all callbacks of the specified event type are unregistered.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.                 |
|801 | Capability not supported. Failed to call ${geoLocationManager.off('locationIconStatusChange')} due to limited device capabilities.          |
|3301000 | The location service is unavailable.        |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  let callback = (code: geoLocationManager.LocationIconStatus): void => {
    console.info('LocationIconStatus: ' + JSON.stringify(code));
  }
  try {
    geoLocationManager.on('locationIconStatusChange', callback);
    geoLocationManager.off('locationIconStatusChange', callback);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.getLocationIconStatus<sup>12+</sup>

getLocationIconStatus(): LocationIconStatus

Obtains the current location icon status.

**System capability**: SystemCapability.Location.Location.Core

**System API**: This is a system API.

**Return value**

  | Type| Description|
  | -------- | -------- |
  | [LocationIconStatus](#locationiconstatus12) | Location icon status.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.getLocationIconStatus} due to limited device capabilities.          |
|3301000  | The location service is unavailable.                  |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    let iconStatus = geoLocationManager.getLocationIconStatus();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.enableLocationByUserId<sup>18+</sup>

enableLocationByUserId(userId: number): Promise&lt;void&gt;

Enables the location switch for the specified system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | userId | number | Yes| System account ID. For details about how to obtain the system account ID, see [Obtaining All System Accounts](../../basic-services/account/manage-os-account-sys.md#obtaining-all-system-accounts).|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.enableLocationByUserId} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    // Enable the location switch for the specified system account. For example, if the account ID is below 101, you can enable the location switch for the account whose ID is 100.
    let userId: number = 100;
    geoLocationManager.enableLocationByUserId(userId).then(() => {
      console.info('promise, enableLocationByUserId succeed');
    })
      .catch((error: BusinessError) => {
        console.error('promise, enableLocationByUserId: error=' + JSON.stringify(error));
      });
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.disableLocationByUserId<sup>18+</sup>

disableLocationByUserId(userId: number): void

Disables the location switch for the specified system account.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_SECURE_SETTINGS and ohos.permission.CONTROL_LOCATION_SWITCH

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | userId | number | Yes| System account ID. For details about how to obtain the system account ID, see [Obtaining All System Accounts](../../basic-services/account/manage-os-account-sys.md#obtaining-all-system-accounts).|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.disableLocationByUserId} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    // Disable the location switch for the specified system account. For example, if the account ID is below 101, you can disable the location switch for the account whose ID is 100.
    let userId: number = 100;
    geoLocationManager.disableLocationByUserId(userId);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.isLocationEnabledByUserId<sup>18+</sup>

isLocationEnabledByUserId(userId: number): boolean

Checks whether the location switch is enabled for the specified system account.

**System API**: This is a system API.

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | userId | number | Yes| System account ID. For details about how to obtain the system account ID, see [Obtaining All System Accounts](../../basic-services/account/manage-os-account-sys.md#obtaining-all-system-accounts).|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | **true**: The location switch is enabled.<br>**false**: The location switch is disabled.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.isLocationEnabledByUserId} due to limited device capabilities.          |
|3301000 | The location service is unavailable. |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    // Check whether the location switch is enabled for the specified system account. For example, if the account ID is below 101, you can check whether the location switch is enabled for the account whose ID is 100.
    let userId: number = 100;
    let locationEnabled = geoLocationManager.isLocationEnabledByUserId(userId);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.setLocationSwitchIgnored<sup>18+</sup>

setLocationSwitchIgnored(isIgnored: boolean): void

Sets whether the location switch is ignored.

If this parameter is set to **true**, the application can obtain the location information when the location switch is disabled. The setting takes effect 2 minutes after the API is successfully called.

**System API**: This is a system API.

**Required permissions**: ohos.permission.LOCATION_SWITCH_IGNORED

**System capability**: SystemCapability.Location.Location.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | isIgnored | boolean | Yes| **true**: The application can obtain location information when the location switch is disabled. The setting takes effect 2 minutes after the API is successfully called.<br>**false**: The application cannot obtain location information when the location switch is disabled.|

**Error codes**

For details about the error codes, see [Location Kit Error Codes](errorcode-geoLocationManager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.setLocationSwitchIgnored} due to limited device capabilities.          |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    let isIgnored: boolean = true;
    geoLocationManager.setLocationSwitchIgnored(isIgnored);
  } catch (err) {
    console.error("errCode:" + err.code + ", message:" + err.message);
  }
  ```


## geoLocationManager.addFusionFence

addFusionFence(fenceRequestParams: FusionFenceRequestParams): Promise&lt;void&gt;

Adds a fused fence and subscribes to fence events. This API uses a promise to return the result asynchronously. Before calling this API, you are advised to call [geoLocationManager.isFusionFenceSupported](#geolocationmanagerisfusionfencesupported) to check whether the corresponding capability is supported.

A fused fence supports setting multiple types of fences, including GNSS fences, Wi-Fi fences, and CELL fences.

**Since:** 26.0.0

**System API:** This API is a system API.

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction:** This API is only available under the stage model.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | fenceRequestParams | FusionFenceRequestParams&lt;[FusionFenceRequestParams](#fusionfencerequestparams)&gt; | Yes | Fused fence request information. |

**Error code**

For details about the following error codes, see [Location service error code](errorcode-geoLocationManager.md).

| Error code ID | Error message |
| -------- | ---------------------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API.                 |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.addFusionFence} due to limited device.          |
|3301000 | The location service is unavailable.                                            |
|3301100 | The location switch is off.|
|3301601 | The number of geofences exceeds the maximum.                                            |
|3501603 | Duplicate fusion fence identifier.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';
  // Create fence request information.
  let latitude = 30.07;
  let longitude = 119.98;
  // Polygon fence location information.
  let point: geoLocationManager.Point = {
    latitude:latitude,
    longitude:longitude
  }
  // Circular fence information, including latitude and longitude, radius, and survival time.
  let geofence: geoLocationManager.Geofence = {
    "latitude": latitude, "longitude": longitude, "radius": 2000, "expiration": 500000000
  }
  // Polygon fence location information set.
  let polygon: Array<geoLocationManager.Point> = [point];
  // GNSS fence request information.
  let gnssFence: geoLocationManager.GnssFence = {
    gnssFenceType: geoLocationManager.GnssFenceType.CIRCULAR, // GnssFenceType
    circularFence: geofence,
    polygon: polygon
  }
  // GNSS fence request information set.
  let gnssFences: Array<geoLocationManager.GnssFence> = [gnssFence];
  // CELL fence information extension field, optional, can be empty.
  let additionsMap: Map<string, string> = new Map<string, string>();
  // CELL information.
  let cellInfo: geoLocationManager.CellInfo = {
    timeSinceBoot:1781062881671, cellId:9999, lac:1024, mcc: 460, mnc: 1, rat: 13, signalIntensity: -75, arfcn: 1850, pci: 256, tac: 888,
    additionsMap: additionsMap
  }
  // CELL information set.
  let cellInfos: Array<geoLocationManager.CellInfo> = [cellInfo];
  // CELL fence request information.
  let cellFence: geoLocationManager.CellFence = {
    cellInfos: cellInfos,
  };
  // CELL fence request information set.
  let cellFences: Array<geoLocationManager.CellFence> = [cellFence];
  // MAC address.
  let mac: Array<string> = ["FA:C4:D0:0E:BF:DF"];
  // Wi-Fi fingerprint information.
  let wifiFeature: geoLocationManager.WirelessSignalFeature = {
    rssiAvg: 1,
    rssiStandardDeviation:2.0,
    mac:mac
  };
  // Wi-Fi fingerprint information set.
  let wifiFeatures: Array<geoLocationManager.WirelessSignalFeature> = [wifiFeature];
  // Wi-Fi fence request information.
  let wifiFence: geoLocationManager.WifiFence = {
    type: geoLocationManager.WifiFingerprintType.LOCATION,
    wifiFeatures:wifiFeatures
  };
  // Wi-Fi fence request information set.
  let wifiFences: Array<geoLocationManager.WifiFence> = [wifiFence];
  // Construct the fence request parameter fenceRequestParams.
  let fenceRequestParams: geoLocationManager.FusionFenceRequestParams = {
    // Fused fence unique identifier.
    identifier: "123456789",
    // Fused fence scenario.
    scene: geoLocationManager.FusionFenceScene.AIRPORT,
    // Fused fence type. For details, see FusionFenceType.
    fenceType: 1,
    // POI type, optional.
    poiType: "1",
    // POI location information.
    poiLocation: point,
    // Fence events to listen for. For details, see GeofenceTransitionEvent. Each bit indicates a fence event. For example, 3 indicates listening for both fence entry and fence exit events.
    monitorTransitionEvents: 63,
    // Indicates the lingering time. The unit is milliseconds.
    loiterTimeMs: 10000,
    // GNSS fence information set, optional. Mandatory if fenceType is GNSS.
    gnssFences: gnssFences,
    // CELL fence information set, optional. Mandatory if fenceType is CELLULAR.
    cellFences: cellFences,
    // Wi-Fi fence information set, optional. Mandatory if fenceType is WIFI.
    wifiFences: wifiFences,
    // Indicates the fence survival time. The unit is milliseconds.
    expirationMs: 100000000,
    // Callback used to receive fence events.
    fenceTransitionCallback: (transition : geoLocationManager.FusionFenceTransition) => {
      if (transition) {
        console.info("GeofenceTransition: ", JSON.stringify(transition));
      }
    },
  }
  try {
    // Add a fence.
    await geoLocationManager.addFusionFence(fenceRequestParams).then(() => {
      // Fence added successfully.
      console.info("addFusionFence success");
    }).catch((error : BusinessError) => {
      console.error("addFusionFence: BusinessError=" + JSON.stringify(error));
    });
  } catch(error) {
    console.error("addFusionFence: error=" + JSON.stringify(error));
  }
  ```


## geoLocationManager.removeFusionFence

removeFusionFence(identifier: string): Promise&lt;void&gt;

Deletes a fused fence and unsubscribes from its events. This API uses a promise to return the result asynchronously. Before calling this API, you are advised to call [geoLocationManager.isFusionFenceSupported](#geolocationmanagerisfusionfencesupported) to check whether the corresponding capability is supported.

**Since:** 26.0.0

**System API**: This API is a system API.

**System capability:** SystemCapability.Location.Location.Geofence

**Model restriction**: This API is only available under the Stage model.

**Parameters**

  | Name | Type | Mandatory | Description |
  | -------- | -------- | -------- | -------- |
  | identifier | string | Yes | Unique identifier of the fused fence. It must be the same as the identifier passed to addFusionFence to successfully delete the fence.|

**Error codes**

For details about the following error codes, see [Location service error code](errorcode-geoLocationManager.md).

| Error code ID | Error message |
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Failed to call ${geoLocationManager.removeFusionFence} due to limited device.          |
|3301000 | The location service is unavailable.                                            |
|3301602 | Failed to delete a fusion fence due to an incorrect identifier.                                          |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    // The identifier must be the same as that passed to addFusionFence to delete the fence successfully.
    let identifier = "123456789";
    await geoLocationManager.removeFusionFence(identifier).then(() => {
      // Fence deleted successfully.
      console.info("removeFusionFence success");
    }).catch((error : BusinessError) => {
      console.error("removeFusionFence: BusinessError=" + JSON.stringify(error));
    });
  } catch(error) {
    console.error("removeFusionFence: error=" + JSON.stringify(error));
  }
  ```


## geoLocationManager.isFusionFenceSupported

isFusionFenceSupported(): boolean

Checks whether the system supports the fused fence capability.

**Since:** 26.0.0

**System API**: This API is a system API.

**System capability:** SystemCapability.Location.Location.Core

**Model restriction:** This API is only available under the Stage model.

**Return value**:

  | Type | Description |
  | -------- | -------- |
  | boolean | true: supports the fused fence capability.<br/>false: does not support the fused fence capability. |
  
  **Error code**:

For details about the following error codes, see [Location service error code](errorcode-geoLocationManager.md).

| Error code ID | Error message |
| -------- | ---------------------------------------- |
|202 | Permission verification failed. A non-system application calls a system API. |
|3301000 | The location service is unavailable.                                            |

**Example**

  ```ts
  import { geoLocationManager } from '@kit.LocationKit';

  try {
    let isFusionFenceSupported = geoLocationManager.isFusionFenceSupported();
  } catch (err) {
    console.error("errCode:" + err.code + ", message:"  + err.message);
  }
  ```