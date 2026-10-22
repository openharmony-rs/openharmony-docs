# @ohos.geoLocationManager

Provides interfaces for acquiring location information, managing location switches, geocoding, reverse geocoding, country code, fencing and other functions.

**Since:** 9

<!--Device-unnamed-declare namespace geoLocationManager--><!--Device-unnamed-declare namespace geoLocationManager-End-->

**System capability:** 
- API version 11 and later: SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addBeaconFence](arkts-location-geolocationmanager-addbeaconfence-f.md#addbeaconfence-1) | Add a beacon fence. |
| [addGnssGeofence](arkts-location-geolocationmanager-addgnssgeofence-f.md#addgnssgeofence-1) | Add a geofence. |
| [findMatchingWlan](arkts-location-geolocationmanager-findmatchingwlan-f.md#findmatchingwlan-1) | Check whether the WLAN scan results match the WLAN BSSID list, return information about the WLAN device that is successfully matched. |
| [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md#flushcachedgnsslocations-1) | All prepared GNSS locations are returned to the application through the callback function, and the bottom-layer buffer is cleared. |
| [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md#flushcachedgnsslocations-2) | All prepared GNSS locations are returned to the application, and the bottom-layer buffer is cleared. |
| [getActiveGeoFences](arkts-location-geolocationmanager-getactivegeofences-f.md#getactivegeofences-1) | Get all active fences. |
| [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md#getaddressesfromlocation-1) | Obtain address info from location. |
| [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md#getaddressesfromlocation-2) | Obtain address info from location. |
| [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md#getaddressesfromlocationname-1) | Obtain latitude and longitude info from location address. |
| [getAddressesFromLocationName](arkts-location-geolocationmanager-getaddressesfromlocationname-f.md#getaddressesfromlocationname-2) | Obtain latitude and longitude info from location address. |
| [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md#getcachedgnsslocationssize-1) | Obtain the number of cached GNSS locations reported at a time. |
| [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md#getcachedgnsslocationssize-2) | Obtain the number of cached GNSS locations. |
| [getCountryCode](arkts-location-geolocationmanager-getcountrycode-f.md#getcountrycode-1) | Obtain the current country code. |
| [getCountryCode](arkts-location-geolocationmanager-getcountrycode-f.md#getcountrycode-2) | Obtain the current country code. |
| [getCurrentDistrict](arkts-location-geolocationmanager-getcurrentdistrict-f.md#getcurrentdistrict-1) | Obtains the information about the district where the current device is located. |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md#getcurrentlocation-1) | Obtain current location. |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md#getcurrentlocation-2) | Obtain current location. |
| [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md#getcurrentlocation-3) | Obtain current location. |
| [getCurrentWifiBssidForLocating](arkts-location-geolocationmanager-getcurrentwifibssidforlocating-f.md#getcurrentwifibssidforlocating-1) | Obtains the BSSID of the connected Wi-Fi hotspot. |
| [getDistanceBetweenLocations](arkts-location-geolocationmanager-getdistancebetweenlocations-f.md#getdistancebetweenlocations-1) | Obtains the distance between two locations. |
| [getGeofenceSupportedCoordTypes](arkts-location-geolocationmanager-getgeofencesupportedcoordtypes-f.md#getgeofencesupportedcoordtypes-1) | Obtains the coordinate system types supported by geofence. |
| [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md#getlastlocation-1) | Obtain last known location. |
| [getPoiInfo](arkts-location-geolocationmanager-getpoiinfo-f.md#getpoiinfo-1) | Obtaining POI Information. |
| [getPostProcessingTrack](arkts-location-geolocationmanager-getpostprocessingtrack-f.md#getpostprocessingtrack-1) | Obtain post-processing trajectory information under specific sport mode. Only [SKIING](arkts-location-geolocationmanager-sportstype-e.md#skiing) is supported currently. |
| [isBeaconFenceSupported](arkts-location-geolocationmanager-isbeaconfencesupported-f.md#isbeaconfencesupported-1) | Check whether the BeaconFence service is supported. |
| [isCachedGnssServiceSupported](arkts-location-geolocationmanager-iscachedgnssservicesupported-f.md#iscachedgnssservicesupported-1) | Check whether the cached GNSS service is supported. |
| [isGeocoderAvailable](arkts-location-geolocationmanager-isgeocoderavailable-f.md#isgeocoderavailable-1) | Obtain geocoding service status. |
| [isGnssFenceServiceSupported](arkts-location-geolocationmanager-isgnssfenceservicesupported-f.md#isgnssfenceservicesupported-1) | Check whether the GNSS fence service is supported. |
| [isGnssServiceSupported](arkts-location-geolocationmanager-isgnssservicesupported-f.md#isgnssservicesupported-1) | Check whether the GNSS service is supported. |
| [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md#islocationenabled-1) | Obtain current location switch status. |
| [isPoiServiceSupported](arkts-location-geolocationmanager-ispoiservicesupported-f.md#ispoiservicesupported-1) | Check whether the POI service is supported. |
| [isWlanBssidMatched](arkts-location-geolocationmanager-iswlanbssidmatched-f.md#iswlanbssidmatched-1) | Check whether the WLAN scan results match the WLAN BSSID list. |
| [off('locationChange')](arkts-location-geolocationmanager-off-f.md#offlocationchange) | Unsubscribe location changed. You are advised to use the [offLocationChange](arkts-location-geolocationmanager-offlocationchange-f.md) instead. |
| [off('locationError')](arkts-location-geolocationmanager-off-f.md#offlocationerror) | Unsubscribe continuous location error changed. |
| [off('locationEnabledChange')](arkts-location-geolocationmanager-off-f.md#offlocationenabledchange) | Unsubscribe location switch changed. |
| [off('cachedGnssLocationsChange')](arkts-location-geolocationmanager-off-f.md#offcachedgnsslocationschange) | Unsubscribe to cache GNSS locations update messages. |
| [off('satelliteStatusChange')](arkts-location-geolocationmanager-off-f.md#offsatellitestatuschange) | Unsubscribe satellite status changed. |
| [off('nmeaMessage')](arkts-location-geolocationmanager-off-f.md#offnmeamessage) | Unsubscribe nmea message changed. |
| [off('gnssFenceStatusChange')](arkts-location-geolocationmanager-off-f.md#offgnssfencestatuschange) | Remove a geofence and unsubscribe geofence status changed. |
| [off('countryCodeChange')](arkts-location-geolocationmanager-off-f.md#offcountrycodechange) | Unregistering the callback function for listening to country code changes. |
| [off('bluetoothScanResultChange')](arkts-location-geolocationmanager-off-f.md#offbluetoothscanresultchange) | Stop bluetooth scanning and unregister to listen to bluetooth scanning result changes. |
| [offLocationChange](arkts-location-geolocationmanager-offlocationchange-f.md#offlocationchange-1) | Unsubscribe location changed. |
| [on('locationChange')](arkts-location-geolocationmanager-on-f.md#onlocationchange) | Subscribe location changed. You are advised to use the [onLocationChange](arkts-location-geolocationmanager-onlocationchange-f.md) instead. |
| [on('locationError')](arkts-location-geolocationmanager-on-f.md#onlocationerror) | Subscribe continuous location error changed. |
| [on('locationEnabledChange')](arkts-location-geolocationmanager-on-f.md#onlocationenabledchange) | Subscribe location switch changed. |
| [on('cachedGnssLocationsChange')](arkts-location-geolocationmanager-on-f.md#oncachedgnsslocationschange) | Subscribe to cache GNSS locations update messages. |
| [on('satelliteStatusChange')](arkts-location-geolocationmanager-on-f.md#onsatellitestatuschange) | Subscribe satellite status changed. |
| [on('nmeaMessage')](arkts-location-geolocationmanager-on-f.md#onnmeamessage) | Subscribe nmea message changed. |
| [on('gnssFenceStatusChange')](arkts-location-geolocationmanager-on-f.md#ongnssfencestatuschange) | Add a geofence and subscribe geofence status changed. |
| [on('countryCodeChange')](arkts-location-geolocationmanager-on-f.md#oncountrycodechange) | Registering the callback function for listening to country code changes. |
| [on('bluetoothScanResultChange')](arkts-location-geolocationmanager-on-f.md#onbluetoothscanresultchange) | Registers and listens to bluetooth scanning results for location services. |
| [onLocationChange](arkts-location-geolocationmanager-onlocationchange-f.md#onlocationchange-1) | Subscribe location changed. |
| [removeBeaconFence](arkts-location-geolocationmanager-removebeaconfence-f.md#removebeaconfence-1) | Remove a beacon fence. |
| [removeGnssGeofence](arkts-location-geolocationmanager-removegnssgeofence-f.md#removegnssgeofence-1) | Remove a geofence. |
| [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md#sendcommand-1) | Send extended commands to location subsystem. |
| [sendCommand](arkts-location-geolocationmanager-sendcommand-f.md#sendcommand-2) | Send extended commands to location subsystem. |
| [startBluetoothSearch](arkts-location-geolocationmanager-startbluetoothsearch-f.md#startbluetoothsearch-1) | Starts Bluetooth scanning and matches the device ID list in the input parameter with the Bluetooth scanning result. If the matching is successful, the Bluetooth device information is returned through the callback. |
| [stopBluetoothSearch](arkts-location-geolocationmanager-stopbluetoothsearch-f.md#stopbluetoothsearch-1) | Stop Bluetooth scanning and searching. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addFusionFence](arkts-location-geolocationmanager-addfusionfence-f-sys.md#addfusionfence-1) | Add a fusion fence. |
| [disableLocation](arkts-location-geolocationmanager-disablelocation-f-sys.md#disablelocation-1) | Disable location switch. |
| [disableLocationByUserId](arkts-location-geolocationmanager-disablelocationbyuserid-f-sys.md#disablelocationbyuserid-1) | Turn off the location switch for a specified user. |
| [disableLocationMock](arkts-location-geolocationmanager-disablelocationmock-f-sys.md#disablelocationmock-1) | Disable the geographical location simulation function. |
| [disableReverseGeocodingMock](arkts-location-geolocationmanager-disablereversegeocodingmock-f-sys.md#disablereversegeocodingmock-1) | Disable the reverse geocoding simulation function. |
| [enableLocation](arkts-location-geolocationmanager-enablelocation-f-sys.md#enablelocation-1) | Enable location switch. |
| [enableLocation](arkts-location-geolocationmanager-enablelocation-f-sys.md#enablelocation-2) | Enable location switch. |
| [enableLocationByUserId](arkts-location-geolocationmanager-enablelocationbyuserid-f-sys.md#enablelocationbyuserid-1) | Turn on the location switch for a specified user. |
| [enableLocationMock](arkts-location-geolocationmanager-enablelocationmock-f-sys.md#enablelocationmock-1) | Enable the geographical location simulation function. |
| [enableReverseGeocodingMock](arkts-location-geolocationmanager-enablereversegeocodingmock-f-sys.md#enablereversegeocodingmock-1) | Enable the reverse geocoding simulation function. |
| [getLocatingRequiredData](arkts-location-geolocationmanager-getlocatingrequireddata-f-sys.md#getlocatingrequireddata-1) | Get WiFi/BT scanning information, and use the WiFi/BT scanning information for localization. |
| [getLocationIconStatus](arkts-location-geolocationmanager-getlocationiconstatus-f-sys.md#getlocationiconstatus-1) | Get location icon status. |
| [isFusionFenceSupported](arkts-location-geolocationmanager-isfusionfencesupported-f-sys.md#isfusionfencesupported-1) | Check whether the fusion fence service is supported. |
| [isLocationEnabledByUserId](arkts-location-geolocationmanager-islocationenabledbyuserid-f-sys.md#islocationenabledbyuserid-1) | Obtaining the location switch status of a specified user. |
| [isLocationPrivacyConfirmed](arkts-location-geolocationmanager-islocationprivacyconfirmed-f-sys.md#islocationprivacyconfirmed-1) | Querying location privacy protocol confirmation status. |
| [off('locatingRequiredDataChange')](arkts-location-geolocationmanager-off-f-sys.md#offlocatingrequireddatachange) | Stop WiFi/BT scanning and unsubscribe from WiFi/BT scanning information changes. |
| [off('locationIconStatusChange')](arkts-location-geolocationmanager-off-f-sys.md#offlocationiconstatuschange) | Unsubscribe location icon status changed. |
| [on('locatingRequiredDataChange')](arkts-location-geolocationmanager-on-f-sys.md#onlocatingrequireddatachange) | Subscribe to changes in WiFi/BT scanning information, and use the WiFi/BT scanning information for localization. |
| [on('locationIconStatusChange')](arkts-location-geolocationmanager-on-f-sys.md#onlocationiconstatuschange) | Subscribe location icon status changed. |
| [removeFusionFence](arkts-location-geolocationmanager-removefusionfence-f-sys.md#removefusionfence-1) | Remove a fusion fence. |
| [setLocationPrivacyConfirmStatus](arkts-location-geolocationmanager-setlocationprivacyconfirmstatus-f-sys.md#setlocationprivacyconfirmstatus-1) | Set location privacy protocol confirmation status. |
| [setLocationSwitchIgnored](arkts-location-geolocationmanager-setlocationswitchignored-f-sys.md#setlocationswitchignored-1) | Set the app locating behavior not controlled by the location switch. |
| [setMockedLocations](arkts-location-geolocationmanager-setmockedlocations-f-sys.md#setmockedlocations-1) | Set the configuration parameters for location simulation. |
| [setReverseGeocodingMockInfo](arkts-location-geolocationmanager-setreversegeocodingmockinfo-f-sys.md#setreversegeocodingmockinfo-1) | Set the configuration parameters for simulating reverse geocoding. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md) | Beacon fence details. |
| [BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md) | Configuring parameters in BeaconFence request. |
| [BeaconManufactureData](arkts-location-geolocationmanager-beaconmanufacturedata-i.md) | Beacon equipment manufacturer data. |
| [BluetoothScanResult](arkts-location-geolocationmanager-bluetoothscanresult-i.md) | Describes the contents of the bluetooth scan results. |
| [BluetoothSearchRequestParams](arkts-location-geolocationmanager-bluetoothsearchrequestparams-i.md) | Indicates request parameters for Bluetooth search function. |
| [CachedGnssLocationsRequest](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md) | Parameters for requesting to report cache location information. |
| [ContinuousLocationRequest](arkts-location-geolocationmanager-continuouslocationrequest-i.md) | Configuring parameters in continuous location requests. |
| [CountryCode](arkts-location-geolocationmanager-countrycode-i.md) | Country code structure. |
| [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md) | Configuring parameters in current location requests. |
| [DistrictInfo](arkts-location-geolocationmanager-districtinfo-i.md) | Indicates request parameters for obtaining the district information. |
| [DistrictRequestParams](arkts-location-geolocationmanager-districtrequestparams-i.md) | Indicates request parameters for obtaining the district information. |
| [GeoAddress](arkts-location-geolocationmanager-geoaddress-i.md) | Data struct describes geographic locations. |
| [GeoCodeRequest](arkts-location-geolocationmanager-geocoderequest-i.md) | Configuring parameters in geocode requests. |
| [Geofence](arkts-location-geolocationmanager-geofence-i.md) | Circular fence information. |
| [GeofenceRequest](arkts-location-geolocationmanager-geofencerequest-i.md) | Configuring parameters in geo fence requests. |
| [GeofenceTransition](arkts-location-geolocationmanager-geofencetransition-i.md) | Geofence transition status. |
| [GnssGeofenceRequest](arkts-location-geolocationmanager-gnssgeofencerequest-i.md) | Configuring parameters in GNSS geofence requests. |
| [Location](arkts-location-geolocationmanager-location-i.md) | Provides information about geographic locations. |
| [LocationCommand](arkts-location-geolocationmanager-locationcommand-i.md) | Location subsystem command structure. |
| [LocationRequest](arkts-location-geolocationmanager-locationrequest-i.md) | Configuring parameters in location requests. |
| [MatchingWlanInfo](arkts-location-geolocationmanager-matchingwlaninfo-i.md) | Matching WLAN information structure. |
| [Poi](arkts-location-geolocationmanager-poi-i.md) | Describes the information about a single POI. |
| [PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md) | Describes the POI information struct. |
| [Point](arkts-location-geolocationmanager-point-i.md) | Indicates a location point, including the longitude and latitude. |
| [ReverseGeoCodeRequest](arkts-location-geolocationmanager-reversegeocoderequest-i.md) | Configuring parameters in reverse geocode requests. |
| [SatelliteStatusInfo](arkts-location-geolocationmanager-satellitestatusinfo-i.md) | Satellite status information. |
| [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | Configuring parameters in single location requests. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BluetoothScanInfo](arkts-location-geolocationmanager-bluetoothscaninfo-i-sys.md) | Describes the contents of the Bluetooth scan results. |
| [CellFence](arkts-location-geolocationmanager-cellfence-i-sys.md) | Indicates CELL fence information. |
| [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md) | Cell information. |
| [FusionFenceRequestParams](arkts-location-geolocationmanager-fusionfencerequestparams-i-sys.md) | Indicates fusion fence request params. |
| [FusionFenceTransition](arkts-location-geolocationmanager-fusionfencetransition-i-sys.md) | Indicates fusion fence transition information. |
| [GeoAddress](arkts-location-geolocationmanager-geoaddress-i-sys.md) | Data struct describes geographic locations. |
| [GnssFence](arkts-location-geolocationmanager-gnssfence-i-sys.md) | Indicates GNSS fence information. |
| [LocatingRequiredData](arkts-location-geolocationmanager-locatingrequireddata-i-sys.md) | Describes the structure of the data required for locating. |
| [LocatingRequiredDataConfig](arkts-location-geolocationmanager-locatingrequireddataconfig-i-sys.md) | Describes the request parameters for obtaining the data required for locating. |
| [LocationMockConfig](arkts-location-geolocationmanager-locationmockconfig-i-sys.md) | Parameters for configuring the location simulation function. |
| [ReverseGeocodingMockInfo](arkts-location-geolocationmanager-reversegeocodingmockinfo-i-sys.md) | Configuration parameters for simulating reverse geocoding. |
| [WifiFence](arkts-location-geolocationmanager-wififence-i-sys.md) | Indicates Wi-Fi fence information. |
| [WifiScanInfo](arkts-location-geolocationmanager-wifiscaninfo-i-sys.md) | Describes the scanned WiFi information. |
| [WirelessSignalFeature](arkts-location-geolocationmanager-wirelesssignalfeature-i-sys.md) | Indicates wireless signal feature. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BeaconFenceInfoType](arkts-location-geolocationmanager-beaconfenceinfotype-e.md) | Enum for the beacon fence information type. |
| [CoordinateSystemType](arkts-location-geolocationmanager-coordinatesystemtype-e.md) | Enum for coordinate system type. |
| [CountryCodeType](arkts-location-geolocationmanager-countrycodetype-e.md) | Enum for country code type. |
| [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md) | Enum for geofence transition status. |
| [LocatingPriority](arkts-location-geolocationmanager-locatingpriority-e.md) | Enum for locating priority. |
| [LocationError](arkts-location-geolocationmanager-locationerror-e.md) | Enum for location error code. |
| [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md) | Enum for location priority. |
| [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md) | Enum for location scenario. |
| [LocationSourceType](arkts-location-geolocationmanager-locationsourcetype-e.md) | Enum for the source of the location. |
| [PowerConsumptionScenario](arkts-location-geolocationmanager-powerconsumptionscenario-e.md) | Enum for power consumption scenario. |
| [SatelliteAdditionalInfo](arkts-location-geolocationmanager-satelliteadditionalinfo-e.md) | Enum for satellite additional information. |
| [SatelliteConstellationCategory](arkts-location-geolocationmanager-satelliteconstellationcategory-e.md) | Enum for satellite constellation category. |
| [SportsType](arkts-location-geolocationmanager-sportstype-e.md) | Enum for sports type |
| [UserActivityScenario](arkts-location-geolocationmanager-useractivityscenario-e.md) | Enum for user activity scenario. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FusionFenceScene](arkts-location-geolocationmanager-fusionfencescene-e-sys.md) | Enum for fusion fence scene. |
| [FusionFenceType](arkts-location-geolocationmanager-fusionfencetype-e-sys.md) | Enum for fusion fence type. |
| [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e-sys.md) | Enum for geofence transition status. |
| [GnssFenceType](arkts-location-geolocationmanager-gnssfencetype-e-sys.md) | Enum for GNSS fence type. |
| [LocatingRequiredDataType](arkts-location-geolocationmanager-locatingrequireddatatype-e-sys.md) | Enum for locating required data type. |
| [LocationIconStatus](arkts-location-geolocationmanager-locationiconstatus-e-sys.md) | Enum for location icon status. |
| [LocationPrivacyType](arkts-location-geolocationmanager-locationprivacytype-e-sys.md) | Enum for location privacy type. |
| [WifiFingerprintType](arkts-location-geolocationmanager-wififingerprinttype-e-sys.md) | Enum for Wi-Fi fingerprint type. |
<!--DelEnd-->
