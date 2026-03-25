# Geocoding and Reverse Geocoding
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->

## Scenario

Describing a location using longitude-latitude coordinates is accurate, but neither intuitive nor user-friendly. To address this issue, the system provides your application the geocoding and reverse geocoding capabilities:

- Geocoding: converts geographic descriptions into specific longitude-latitude coordinates.

- Reverse geocoding: converts specific longitude-latitude coordinates into geographic descriptions.

The geocoding information describes a location using several attributes, including the country, administrative region, street, house number, and address, etc.

## Available APIs

The following table lists the APIs for mutual conversion between longitude-latitude coordinates and geocoding information. For details, see [Location Kit API reference](../../reference/apis-location-kit/js-apis-geoLocationManager.md).

| API| Description| 
| -------- | -------- |
| [isGeocoderAvailable(): boolean](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagerisgeocoderavailable) | Checks whether the geocoding and reverse geocoding services are available.| 
| [getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocation) | Converts coordinates into geographic descriptions through reverse geocoding. This API uses an asynchronous callback to return the result. | 
| [getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocationname) | Converts geographic descriptions into coordinates through geocoding. This API uses an asynchronous callback to return the result. | 

## How to Develop

> **NOTE**
> The geocoding and reverse geocoding services need to access backend services to obtain information. Therefore, before performing the following steps, ensure that your device is connected to the network.

1. Import the **geoLocationManager** module. All geocoding and reverse geocoding APIs are provided by this module.
   
   ```ts
   import { geoLocationManager } from '@kit.LocationKit';
   ```

2. Check whether the geocoding and reverse geocoding services are available.
   - Call **isGeocoderAvailable** to check whether the geocoding and reverse geocoding services are available. If yes, go to step 3. If the services are unavailable, the device does not have the geocoding and reverse geocoding capabilities. Do not use related APIs.
     
      ```ts
      import { geoLocationManager } from '@kit.LocationKit';
      try {
          let isAvailable = geoLocationManager.isGeocoderAvailable();
      } catch (err) {
          console.error("errCode:" + JSON.stringify(err));
      }
      ```

3. Obtain the geocoding conversion result.
   - Call **getAddressesFromLocation** to convert the longitude-latitude coordinates into geocoding information (location information). Your application can obtain the list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the specified coordinates and then read location information from it.
     
      ```ts
      let reverseGeocodeRequest:geoLocationManager.ReverseGeoCodeRequest = {"latitude": 31.12, "longitude": 121.11, "maxItems": 1};
      try {
          geoLocationManager.getAddressesFromLocation(reverseGeocodeRequest, (err, data) => {
              if (err) {
                  console.error('getAddressesFromLocation err: ' + JSON.stringify(err));
              } else {
                  console.info('getAddressesFromLocation data: ' + JSON.stringify(data));
              }
          });
      } catch (err) {
          console.error("errCode:" + JSON.stringify(err));
      }
      ```

   - Call **getAddressesFromLocationName** to convert the geocoding information into longitude-latitude coordinates.
     
      ```ts
      let geocodeRequest:geoLocationManager.GeoCodeRequest = {"description": "No. xx, xx Road, Pudong District, Shanghai", "maxItems": 1};
      try {
          geoLocationManager.getAddressesFromLocationName(geocodeRequest, (err, data) => {
              if (err) {
                  console.error('getAddressesFromLocationName err: ' + JSON.stringify(err));
              } else {
                  console.info('getAddressesFromLocationName data: ' + JSON.stringify(data));
              }
          });
      } catch (err) {
          console.error("errCode:" + JSON.stringify(err));
      }
      ```

      Your application can obtain the list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the specified location information and then read coordinates from it.

      If the location information contains duplicate location names, you can call [GeoCodeRequest](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geocoderequest) to specify a longitude and latitude range to narrow down the scope.
