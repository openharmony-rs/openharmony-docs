# Geocoding and Reverse Geocoding
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=24cb7130c2fa26539d2271d78e3dd3f951ea41dd translatedAt=2026-11-28T02:51:54.480Z nl=1 -->

## Scenario

Describing a location by latitude and longitude is highly accurate but not intuitive or user-friendly. The system provides the following two conversion capabilities:

- Geocoding: Converts a geocode into specific latitude and longitude coordinates.

- Reverse geocoding: Converts specific latitude and longitude coordinates into a geocode.

A geocode contains multiple attributes that describe location information, such as country, administrative division, street, house number, and address description, making the information easier for users to understand.

## Available APIs

The APIs used for conversion between latitude and longitude coordinates and geocodes are described below. For details, see [@ohos.geoLocationManager (Geolocation Manager)](../../reference/apis-location-kit/js-apis-geoLocationManager.md).

| API| Description| 
| -------- | -------- |
| [isGeocoderAvailable(): boolean](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagerisgeocoderavailable) | Checks whether the geocoding and reverse geocoding services are available.| 
| [getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocation) | Converts coordinates into geographic descriptions through reverse geocoding. This API uses an asynchronous callback to return the result. | 
| [getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocationname) | Converts geographic descriptions into coordinates through geocoding. This API uses an asynchronous callback to return the result. | 

## How to Develop

> **NOTE**
> The geocoding and reverse geocoding services need to access backend services. Ensure that your device is connected to the network to obtain information.

1. Import the **geoLocationManager** module. All functional APIs related to geocoding and reverse geocoding capabilities are provided by this module.
   
   <!-- @[geocode_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeocodePage.ets) -->

   ``` TypeScript
   import { geoLocationManager } from '@kit.LocationKit';
   ```

2. Define the geocoding parameters.

   ``` TypeScript
   let latitude: number = 31.12;
   let longitude: number = 121.11;
   let description: string = 'Zhangjiang Road, Pudong New Area, Shanghai';
   ```

3. Check whether the geocoding and reverse geocoding services are available.
   - Call **isGeocoderAvailable** to check whether the geocoding and reverse geocoding services are available. If yes, proceed to step 4. If the services are unavailable, the device does not have the geocoding and reverse geocoding capabilities. Do not use the related APIs.
     
     <!-- @[geocode_is_available](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeocodePage.ets) -->

      ``` TypeScript
      try {
        let isAvailable = geoLocationManager.isGeocoderAvailable();
        if (!isAvailable) {
            console.error('current device do not support geocoder');
        }
        // ...
      } catch (err) {
        console.error('errCode:' + err.code + ', message:'  + err.message);
        // ...
      }
      ```

4. Obtain the geocoding conversion result.
   - Call **getAddressesFromLocation** to convert coordinates into a list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the coordinates.
     
     <!-- @[geocode_reverse_geocode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeocodePage.ets) -->

      ``` TypeScript
      let reverseGeocodeRequest: geoLocationManager.ReverseGeoCodeRequest = {'latitude': latitude, 'longitude': longitude, 'maxItems': 1};
      try {
        if (geoLocationManager.isGeocoderAvailable()) {
          geoLocationManager.getAddressesFromLocation(reverseGeocodeRequest, (err,data) => {
            if (err) {
              console.error('getAddressesFromLocation errCode:' + err.code + ', message:'  + err.message);
            } else {
              console.info('getAddressesFromLocation data: ' + JSON.stringify(data));
            }
            // ...
          });
        }
      } catch (err) {
        console.error('errCode:' + err.code + ', message:'  + err.message);
        // ...
      }
      ```

   - Call **getAddressesFromLocationName** to convert geographic descriptions (i.e., location information) into coordinates.
     
     <!-- @[geocode_forward_geocode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeocodePage.ets) -->

      ``` TypeScript
      let geocodeRequest: geoLocationManager.GeoCodeRequest = {'description': description, 'maxItems': 1};
      try {
        if (geoLocationManager.isGeocoderAvailable()) {
          geoLocationManager.getAddressesFromLocationName(geocodeRequest, (err, data) => {
            if (err) {
              console.error('getAddressesFromLocationName errCode:' + err.code + ', message:'  + err.message);
            } else {
              console.info('getAddressesFromLocationName data: ' + JSON.stringify(data));
            }
            // ...
          });
        }
      } catch (err) {
          console.error('errCode:' + err.code + ', message:'  + err.message);
          // ...
      }
      ```

      Your application can obtain the list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the location information, which contains the corresponding coordinate data.

      If the location description to be queried may have duplicate names in multiple places, you can set [GeoCodeRequest](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geocoderequest) to specify a longitude and latitude range to efficiently obtain the desired accurate results.