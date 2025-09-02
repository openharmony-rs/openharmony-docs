# Using Motion and Orientation Sensors

## Overview

The motion and orientation sensors, such as an accelerometer and a gyroscope, can monitor the motion status and orientation change (such as rotation and tilt) of the device.
Through the W3C standards-compliant API, the **Web** component can access the sensor data to implement richer user interaction features. For example, in a web application, you can use an accelerometer to identify the motion mode and instruct the user to exercise, and use a gyroscope to capture the tilt and rotation of the device in the hand of the player, implementing game experience without button control.

To access the motion and orientation sensors, invoke the following W3C standards-compliant APIs in JavaScript:

| API                     | Name        | Description                                                                                                                                                    |
| ------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Accelerometer             | Accelerometer      | Obtains acceleration data in the X, Y, and Z axes.                                                                                                                   |
| Gyroscope                 | Gyroscope      | Obtains angular velocity data in the X, Y, and Z axes.                                                                                                                   |
| AbsoluteOrientationSensor | Absolute orientation    | Obtains the quaternion including the X, Y, Z, and W components that indicates the absolute orientation of the device.                                                                                                |
| RelativeOrientationSensor | Relative orientation    | Obtains the quaternion including the X, Y, Z, and W components that indicates the relative orientation of the device.                                                                                                |
| DeviceMotionEvent         | Device motion event| Listens for the device motion events to obtain the acceleration data of the device in the X, Y, and Z axes, acceleration data that contains gravity in the X, Y, and Z axes, and rotation rate data of the device in the alpha, beta, and gamma axes.|
| DeviceOrientationEvent    | Device orientation event| Listens for the device orientation events to obtain the angles of the device around the X, Y, and Z axes.                                                                                                           |

## Required Permission

To use the preceding APIs, you need to declare the corresponding sensor permissions in the **module.json5** file. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

```
    "requestPermissions":[
      {
        "name": "ohos.permission.ACCELEROMETER" // Accelerometer permission
      },
      {
        "name": "ohos.permission.GYROSCOPE"      // Gyroscope permission
      }
    ]
```

When the **Web** component is connected to a motion or orientation sensor, configure [onPermissionRequest](../reference/apis-arkweb/ts-basic-components-web-events.md#onpermissionrequest9) to receive permission request notifications.

## How to Develop

1. In the application code, configure [onPermissionRequest](../reference/apis-arkweb/ts-basic-components-web-events.md#onpermissionrequest9) for the **Web** component and use the [getAccessibleResource](../reference/apis-arkweb/ts-basic-components-web.md#getaccessibleresource9) API of [PermissionRequest](../reference/apis-arkweb/ts-basic-components-web.md#permissionrequest9) to obtain the resource type of the request permission. When the resource type is **TYPE_SENSOR**, the sensor is authorized.

   ```ts
   import { webview } from '@kit.ArkWeb';
   import { abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   @Entry
   @Component
   struct WebComponent {
     controller: webview.WebviewController = new webview.WebviewController();
     uiContext: UIContext = this.getUIContext();

     aboutToAppear() {
       // Enable web frontend page debugging.
       webview.WebviewController.setWebDebuggingAccess(true);
       // Create an **AtManager** instance, which is used for application access control.
       let atManager = abilityAccessCtrl.createAtManager();
       try {
         atManager.requestPermissionsFromUser(this.uiContext.getHostContext(), ['ohos.permission.ACCELEROMETER', 'ohos.permission.GYROSCOPE']
           , (err: BusinessError, data: PermissionRequestResult) => {
           console.info('data permissions:' + data.permissions);
           console.info('data authResults:' + data.authResults);
         })
       } catch (error) {
         console.error(`ErrorCode: ${(error as BusinessError).code}, Message: ${(error as BusinessError).message}`);
       }
     }
   
     build() {
       Column() {
         Web({ src: $rawfile('index.html'), controller: this.controller })
           .onPermissionRequest((event) => {
             if (event) {
                this.uiContext.showAlertDialog({
                 title: 'title',
                 message: 'text',
                 primaryButton: {
                   value: 'deny',
                   action: () => {
                     event.request.deny();
                   }
                 },
                 secondaryButton: {
                   value: 'onConfirm',
                   action: () => {
                     event.request.grant(event.request.getAccessibleResource());
                   }
                 },
                 autoCancel: false,
                 cancel: () => {
                   event.request.deny();
                 }
               })
             }
           })
       }
     }
   }
   ```

2. In the frontend page code, use JavaScript to call the W3C standards-compliant API related to the sensor.

   ```html
   <!DOCTYPE HTML>
   <html>
   <head>
       <meta charset="utf-8" />
       <meta name="viewport" content="initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
       <meta name="misapplication-tap-highlight" content="no" />
       <meta name="HandheldFriendly" content="true" />
       <meta name="MobileOptimized" content="320" />
       <title>Motion and direction sensor</title>
       <meta charset="UTF-8">
       <style>
           body {
               font-family: Arial, sans-serif;
           }
       </style>
       <script type="text/javascript">
           // Access the accelerometer of the device and obtain its data.
           function getAccelerometer() {
               var acc = new Accelerometer({frequency: 60});
               acc.addEventListener('activate', () => console.log('Ready to measure.'));
               acc.addEventListener('error', error => console.log('Error type: ' + error.type + ', error: ' + error.error ));
               acc.addEventListener('reading', () => {
                   console.log(`Accelerometer ${acc.timestamp}, ${acc.x}, ${acc.y}, ${acc.z}.`);
               });
               acc.start();
           }
   
           // Access the gyroscope of the device and obtain its data.
           function getGyroscope() {
               var gyr = new Gyroscope({frequency: 60});
               gyr.addEventListener('activate', () => console.log('Ready to measure.'));
               gyr.addEventListener('error', error => console.log('Error type: ' + error.type + ', error: ' + error.error ));
               gyr.addEventListener('reading', () => {
                   console.log(`Gyroscope ${gyr.timestamp}, ${gyr.x}, ${gyr.y}, ${gyr.z}.`);
               });
               gyr.start();
           }
   
           // Access the orientation sensor of the device and obtain its data.
           function getAbsoluteOrientationSensor() {
               var aos = new AbsoluteOrientationSensor({frequency: 60});
               aos.addEventListener('activate', () => console.log('Ready to measure.'));
               aos.addEventListener('error', error => console.log('Error type: ' + error.type + ', error: ' + error.error ));
               aos.addEventListener('reading', () => {
                   console.log(`AbsoluteOrientationSensor data: ${aos.timestamp}, ${aos.quaternion}`);
               });
               aos.start();
           }
   
           // Listen for the motion events of the device and execute the corresponding processing logic.
           function listenDeviceMotionEvent() {
               removeDeviceMotionEvent();
               if ('DeviceMotionEvent' in window) {
                   window.addEventListener('devicemotion', handleMotionEvent, false);
               } else {
                 console.log ("DeviceMotionEvent is not supported.");
               }
           }
   
           // Remove the device motion event listener.
           function removeDeviceMotionEvent() {
               if ('DeviceMotionEvent' in window) {
                 window.removeEventListener('devicemotion', handleMotionEvent, false);
               } else {
                 console.log ("DeviceOrientationEvent is not supported.");
               }
           }
   
           // Handle the motion event.
           function handleMotionEvent(event) {
               const x = event.accelerationIncludingGravity.x;
               const y = event.accelerationIncludingGravity.y;
               const z = event.accelerationIncludingGravity.z;
               console.log(`DeviceMotionEvent data: ${event.timeStamp}, ${x}, ${y}, ${z}`);
           }
   
           // Listen for the device orientation events and execute the corresponding processing logic.
           function listenDeviceOrientationEvent() {
               removeDeviceOrientationEvent();
               if ('DeviceOrientationEvent' in window) {
                   window.addEventListener('deviceorientation', handleOrientationEvent, false);
               } else {
                   console.log ("DeviceOrientationEvent is not supported.");
               }
           }
   
           // Remove the device orientation event listener.
           function removeDeviceOrientationEvent() {
               if ('DeviceOrientationEvent' in window) {
                 window.removeEventListener('deviceorientation', handleOrientationEvent, false);
               } else {
                 console.log ("DeviceOrientationEvent is not supported.");
               }
           }
   
           // Listen for the device orientation events and execute the corresponding processing logic.
           function listenDeviceOrientationEvent2() {
               removeDeviceOrientationEvent2();
               if ('DeviceOrientationEvent' in window) {
                   window.addEventListener('deviceorientationabsolute', handleOrientationEvent, false);
               } else {
                   console.log ("DeviceOrientationEvent is not supported.");
               }
           }
   
           // Remove the device orientation event listener.
           function removeDeviceOrientationEvent2() {
               if ('DeviceOrientationEvent' in window) {
                 window.removeEventListener('deviceorientationabsolute', handleOrientationEvent, false);
               } else {
                 console.log ("DeviceOrientationEvent is not supported.");
               }
           }
   
           // Handle the orientation event.
           function handleOrientationEvent(event) {
               console.log(`DeviceOrientationEvent data: ${event.timeStamp}, ${event.absolute}, ${event.alpha}, ${event.beta}, ${event.gamma}`);
           }
       </script>
   </head>
   <body>
   <div id="dcontent" class="dcontent">
       <h3>Motion and orientation:</h3>
       <ul class="dlist">
           <li><button type="button" onclick="getAccelerometer()">Accelerometer</button></li>;
           <li><button type="button" onclick="getGyroscope()">Gyroscope</button></li>
           <li><button type="button" onclick="getAbsoluteOrientationSensor()">Device (absolute) orientation</button></li>;
           <li><button type="button" onclick="listenDeviceMotionEvent()">Device motion event</button></li>;
           <li><button type="button" onclick="listenDeviceOrientationEvent()">Device orientation event</button></li>;
           <li><button type="button" onclick="listenDeviceOrientationEvent2()">Device (absolute) orientation event</button></li>;
       </ul>
   </div>
   </body>
   </html>
   ```
