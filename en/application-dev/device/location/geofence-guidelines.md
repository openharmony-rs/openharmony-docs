# Geofencing Development Based on Device Location
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=24cb7130c2fa26539d2271d78e3dd3f951ea41dd translatedAt=2026-11-28T02:51:54.480Z nl=1 -->

## Scenario

A geofence is a group of virtual bounds defining an area on the map. When a user device enters or leaves a geofence, your app on the user device can automatically receive notifications and alarms.

Currently, only circular fences are supported. In addition, the geofencing function of the GNSS chip is required. Events of entering or leaving the fence can be accurately identified only in open outdoor areas.

A typical application of geofencing is to create a geofence around an enterprise for targeted advertising. In different areas, you can provide differentiated promotions for mobile devices.

## Available APIs

The following table lists the APIs used in geofencing. For details, see [@ohos.geoLocationManager (Geolocation Manager)](../../reference/apis-location-kit/js-apis-geoLocationManager.md).

| API| Description| 
| -------- | -------- |
| [addGnssGeofence(fenceRequest: GnssGeofenceRequest): Promise&lt;number&gt;](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanageraddgnssgeofence12) | Adds a GNSS geofence and subscribes to geofence transition events. This API uses a promise to return the result.| 
| [removeGnssGeofence(geofenceId: number): Promise&lt;void&gt;](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagerremovegnssgeofence12) | Removes a GNSS geofence and unsubscribes from geofence transition events. This API uses a promise to return the result.| 

## How to Develop

1. Declare the **ohos.permission.APPROXIMATELY_LOCATION** permission. For details, see [Applying for Location Permissions](location-permission-guidelines.md).

2. Import the **geoLocationManager**, **wantAgent**, and **BusinessError** modules.

   <!-- @[geofence_import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   import { geoLocationManager } from '@kit.LocationKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { notificationManager } from '@kit.NotificationKit';
   ```

3. Check whether the geofence feature is supported.

   <!-- @[is_gnss_geofence_support](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   let isGnssGeoFeceSupported = geoLocationManager.isGnssFenceServiceSupported();
   if (!isGnssGeoFeceSupported) {
     console.error('Current Device Do not Support GnssGeofence');
   }
   ```

4. Define the geofence parameters.

   ``` TypeScript
   let fenceId: number = 1;
   let geofence: geoLocationManager.Geofence = {
     "latitude": 34.12, "longitude": 124.11, "radius": 10000.0, "expiration": 10000.0
   }
   ```

5. Specify the types of geofence transition events to listen for. Geofence entry and exit events are used as an example.

   <!-- @[geofence_transition_events](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   let transitionStatusList: geoLocationManager.GeofenceTransitionEvent[] = [
     geoLocationManager.GeofenceTransitionEvent.GEOFENCE_TRANSITION_EVENT_ENTER,
     geoLocationManager.GeofenceTransitionEvent.GEOFENCE_TRANSITION_EVENT_EXIT,
   ];
   ```

6. Create a notification object for **GEOFENCE_TRANSITION_EVENT_ENTER** and **GEOFENCE_TRANSITION_EVENT_EXIT**.

   <!-- @[geofence_notifications](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   // GEOFENCE_TRANSITION_EVENT_ENTER event
   let notificationRequest1: notificationManager.NotificationRequest = {
     id: 1,
     content: {
       notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
       normal: {
         title: 'Geofence Notification',
         text: 'Geofence Entry',
         additionalText: ''
       }
     }
   };
   // Create a notification object for GEOFENCE_TRANSITION_EVENT_EXIT.
   let notificationRequest2: notificationManager.NotificationRequest = {
     id: 2,
     content: {
       notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
       normal: {
         title: 'Geofence Notification',
         text: 'Geofence Exit',
         additionalText: ''
       }
     }
   };
   ```

7. Add a geofence.

   <!-- @[geofence_add_fence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   // Save the created notification objects to Array in the same sequence as in transitionStatusList.
   let notificationRequestList: notificationManager.NotificationRequest[] =
     [notificationRequest1, notificationRequest2];
   // Construct a gnssGeofenceRequest object.
   let gnssGeofenceRequest: geoLocationManager.GnssGeofenceRequest = {
     // Geofence attributes, including the circle center and radius.
     geofence: geofence,
     // Specify the types of geofence transition events to listen for.
     monitorTransitionEvents: transitionStatusList,
     // Specify the notification objects for geofence transition events. This parameter is optional.
     notifications: notificationRequestList,
     // Specify the callback used to receive geofence transition events.
     geofenceTransitionCallback: (err : BusinessError, transition : geoLocationManager.GeofenceTransition) => {
       if (err) {
         console.error('geofenceTransitionCallback: err=' + JSON.stringify(err));
       }
       if (transition) {
         console.info('GeofenceTransition: ' + JSON.stringify(transition));
       }
     }
     // ...
   }
   try {
     // Add a geofence.
     if (geoLocationManager.isGnssFenceServiceSupported()) {
       geoLocationManager.addGnssGeofence(gnssGeofenceRequest).then((id) => {
         // Return the geofence ID after the geofence is added successfully.
         console.info('addGnssGeofence success, fence id: ' + id);
         // ... 
         fenceId = id;
       }).catch((err: BusinessError) => {
         console.error('addGnssGeofence failed, promise errCode:' + (err as BusinessError).code +
           ',errMessage:' + (err as BusinessError).message);
         // ... 
       });
     }
   } catch(error) {
     console.error('addGnssGeofence failed, err:' + JSON.stringify(error));
     // ...
   }
   ```

8. Delete a geofence.

   <!-- @[geofence_remove_fence](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/LocationKit/entry/src/main/ets/location/pages/GeofencePage.ets) -->

   ``` TypeScript
   // fenceId is obtained after geoLocationManager.addGnssGeofence is successfully executed.
   try {
     if (geoLocationManager.isGnssFenceServiceSupported()) {
       geoLocationManager.removeGnssGeofence(fenceId).then(() => {
         console.info('removeGnssGeofence success fenceId:' + fenceId);
         // ...
       }).catch((error : BusinessError) => {
         console.error('removeGnssGeofence: error=' + JSON.stringify(error));
         // ...
       });
     }
   } catch(error) {
     console.error('removeGnssGeofence: error=' + JSON.stringify(error));
     // ...
   }
   ```