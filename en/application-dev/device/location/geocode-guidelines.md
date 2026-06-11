# Geocoding and Reverse Geocoding

<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=a1b9555ca35e53d2ce1fb3e822613b1436be9250 translatedAt=2026-06-08T06:14:46.253Z pushedAt=2026-06-08T13:03:13.281Z -->

## Scenario

Describing a location by latitude and longitude is highly accurate but not intuitive or user-friendly. The system provides the following two conversion capabilities:

- Forward geocoding: Converts a geocode into specific latitude and longitude coordinates.

- Reverse geocoding: Converts specific latitude and longitude coordinates into a geocode.

A geocode contains multiple attributes that describe location information, such as country, administrative division, street, house number, and address description, making the information easier for users to understand.

## Available APIs

The APIs used for conversion between latitude and longitude coordinates and geocodes are described below. For details, see Location Kit API Reference: [@ohos.geoLocationManager (Geolocation Manager)](../../reference/apis-location-kit/js-apis-geoLocationManager.md).

| API| Description| 
| -------- | -------- |
| [isGeocoderAvailable(): boolean](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagerisgeocoderavailable) | Checks whether the geocoding and reverse geocoding services are available.| 
| [getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocation) | Converts coordinates into geographic descriptions and asynchronously returns the result through a callback. | 
| [getAddressesFromLocationName(request: GeoCodeRequest, callback: AsyncCallback&lt;Array&lt;GeoAddress&gt;&gt;): void](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetaddressesfromlocationname) | Converts a geographic description into specific coordinates and asynchronously returns the result through a callback. | 

## How to Develop

> **NOTE**
> The forward geocoding and reverse geocoding services need to access backend services. Ensure that your device is connected to the network to obtain information.

1. Import the **geoLocationManager** module. All functional APIs related to forward geocoding and reverse geocoding capabilities are provided by this module.

   ```ts
   import { geoLocationManager } from '@kit.LocationKit';
   ```

2. Check whether the forward geocoding and reverse geocoding services are available.

   - Call **isGeocoderAvailable** to check whether the forward geocoding and reverse geocoding services are available. If yes, proceed to step 3. If the services are unavailable, the device does not have the geocoding and reverse geocoding capabilities. Do not use the related APIs.

      ```ts
      import { geoLocationManager } from '@kit.LocationKit';
      try {
          let isAvailable = geoLocationManager.isGeocoderAvailable();
      } catch (err) {
          console.error("errCode:" + JSON.stringify(err));
      }
      ```

3. Obtain the geocoding conversion result.

   - Call **getAddressesFromLocation** to convert coordinates into geographic descriptions (i.e., location information). Your application can obtain the list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the coordinates and read the corresponding parameter data based on actual usage requirements.

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

   - Call **getAddressesFromLocationName** to convert geographic descriptions (i.e., location information) into coordinates.

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

      Your application can obtain the list of [GeoAddress](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geoaddress) objects that match the location information, which contains the corresponding coordinate data.

      If the location description to be queried may have duplicate names in multiple places, you can set [GeoCodeRequest](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geocoderequest) to specify a longitude and latitude range to efficiently obtain the desired accurate results.