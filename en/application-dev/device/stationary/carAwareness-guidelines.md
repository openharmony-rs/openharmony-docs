# Vehicle Awareness Development

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=561a48f0279b682322ad16aa122a3161b679e716 translatedAt=2026-08-20T06:28:04.727Z pushedAt=2026-08-20T13:37:15.577Z -->

## Overview

The `carAwareness` (vehicle awareness) module provides camera-based environment and motion awareness capabilities for in-vehicle apps.

For detailed API description, refer to [@ohos.multimodalAwareness.carAwareness (Vehicle Awareness)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-carAwareness.md).

## Air Gesture Awareness Development

### When to Use

Air gesture awareness obtains the coordinates and motion events of the user's hand on the screen. It applies to scenarios such as contactless control of the in-vehicle center console and gesture interaction in interactive games.

### Available APIs

| API Name | Description |
| ------ | ---- |
| onSpatialMotion(callback: Callback\<SpatialMotionInfo\>): void; | Enables air gesture awareness and subscribes to air gesture awareness results. |
| offSpatialMotion(callback?: Callback\<SpatialMotionInfo\>): void; | Disables air gesture awareness and unsubscribes from the results. |
| getAllCapabilityList(): Promise\<Capability[]\>; | Obtains the list of all vehicle awareness capabilities supported by the current device. |

### Required Permission

To use air gesture awareness, the following permission is required: `ohos.permission.vehicle.MMA_SPATIALACTION`.

For details about how to request the permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_SPATIALACTION",
    // Fill in reason and usedScene as needed.
    "reason" : "", // Used for application release verification.
    "usedScene" : {
        "abilities" : [
          "" // Name of the permission to use.
        ],
        "when" : "" // When to call.
    },
  }
]
```

### Parameter Description

**SpatialMotionInfo**

| Name | Type | Description |
| ------ | ---- | ---- |
| timestamp | number | Timestamp of the recognition result, in milliseconds |
| pointX | number | X-axis coordinate of the hand on the screen |
| pointY | number | Y-axis coordinate of the hand on the screen |
| event | number | Gesture event type:<br>-1: Invalid <br>0: Ready<br> 1: Move<br> 2: Tap |

### Constraints

- Depends on the rear camera. If the capability is not supported, error code 34000002, indicating that the specified capability is not supported, is returned.

- Recognition fails when the camera is blocked or the user's gesture is outside the recognition area.

### How to Develop

1. Import the required module.

   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Check whether the device supports the air gesture capability.

   <!-- @[spatialMotion_query](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   async function querySpatialMotionCapability(): Promise<boolean> {
     try {
       const capabilityList = await carAwareness.getAllCapabilityList();
       const isSupported = capabilityList.includes(carAwareness.Capability.SPATIAL_MOTION);
       hilog.info(DOMAIN, TAG, 'Spatial motion supported: %{public}s', isSupported);
       return isSupported;
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to get capability list, error code: %{public}d', err.code);
       return false;
     }
   }
   ```

3. Register the gesture awareness callback to process the recognition result.

   <!-- @[spatialMotion_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function subscribeSpatialMotion(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onSpatialMotion((motionInfo: carAwareness.SpatialMotionInfo) => {
         const eventType: string = getSpatialMotionEventType(motionInfo.event);
         const dataStr: string = `Event: ${eventType}, Position: (${motionInfo.pointX}, ${motionInfo.pointY})`;
         hilog.info(DOMAIN, TAG, 'Spatial motion event: %{public}d', motionInfo.event);
         hilog.info(DOMAIN, TAG, 'Hand coordinate: (%{public}d, %{public}d)', motionInfo.pointX, motionInfo.pointY);
         onUpdate(dataStr);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing spatial motion.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe spatial motion, error code: %{public}d', err.code);
     }
   }
   ```

4. Unsubscribe from gesture awareness.

   <!-- @[spatialMotion_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function unsubscribeSpatialMotion(): void {
     try {
       carAwareness.offSpatialMotion();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing spatial motion.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe spatial motion, error code: %{public}d', err.code);
     }
   }
   ```

## Real-time Weather Awareness Development

### When to Use

Real-time weather awareness obtains the weather conditions of the vehicle's current environment. It applies to scenarios such as adjusting in-vehicle service recommendations based on the weather and automatically enabling wipers or defogging.

### Available APIs

| Name | Description |
| ------ | ---- |
| onRealTimeWeather(callback: Callback\<RealTimeWeatherInfo\>): void; | Enables real-time weather awareness and subscribes to real-time weather awareness results. |
| offRealTimeWeather(callback?: Callback\<RealTimeWeatherInfo\>): void; | Disables real-time weather awareness and unsubscribes from the results. |

### Required Permission

To use real-time weather awareness, the following permission is required: `ohos.permission.vehicle.MMA_WEATHER`.

For details about how to request the permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_WEATHER"
  }
]
```

### Parameter Description

**RealTimeWeatherInfo**

| Name | Type | Description |
| ------ | ---- | ---- |
| timestamp | number | Recognition result timestamp, in milliseconds |
| weather | number | Weather status:<br>-1: Invalid<br> 0: Sunny/Cloudy<br> 1: Mist<br> 2: Dense fog <br>3: Light snow<br> 4: Heavy snow<br> 5: Light rain<br> 6: Heavy rain |

### Constraints

- Depends on the exterior camera. If the exterior camera is unavailable, an error code indicating that the capability is not supported is returned.

- Only the real-time weather at the current vehicle location can be recognized.

### How to Develop

1. Import the required module.

   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Register the weather awareness callback.

   <!-- @[realTimeWeather_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function subscribeWeather(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onRealTimeWeather((weatherInfo: carAwareness.RealTimeWeatherInfo) => {
         const weatherType: string = getWeatherType(weatherInfo.weather);
         hilog.info(DOMAIN, TAG, 'Weather code: %{public}d', weatherInfo.weather);
         onUpdate(weatherType);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing realtime weather.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe realtime weather, error code: %{public}d', err.code);
     }
   }
   ```

3. Unsubscribe from weather awareness.

   <!-- @[realTimeWeather_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function unsubscribeWeather(): void {
     try {
       carAwareness.offRealTimeWeather();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing realtime weather.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe realtime weather, error code: %{public}d', err.code);
     }
   }
   ```

## Refueling Status Awareness Development

### When to Use

Refueling status awareness can identify the start and end states of vehicle refueling. It is suitable for automatically recording the refueling duration, matching and generating refueling orders, and supports atomic service invocation.

### Available APIs

| API Name | Description |
| ------ | ---- |
| onRefueling(callback: Callback\<RefuelingInfo\>): void; | Enables refueling awareness and subscribes to refueling status awareness results. |
| offRefueling(callback?: Callback\<RefuelingInfo\>): void; | Disables refueling awareness and unsubscribes. |

### Required Permission

To use refueling status awareness, the following permission is required: `ohos.permission.vehicle.MMA_ENERGYREFILL`.

For details about how to request the permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

```JSON5
"requestPermissions": [
  {
    "name": "ohos.permission.vehicle.MMA_ENERGYREFILL"
  }
]
```

### Parameter Description

**RefuelingInfo**

| Name | Type | Description |
| ------ | ---- | ---- |
| timestamp | number | Timestamp of the recognition result, in milliseconds. |
| status | number | Refueling status:<br>-1: Invalid <br>0: Idle<br> 1: Refueling started<br> 2: Refueling ended |

### Constraints

- Depends on the exterior camera. If the exterior camera is unavailable, an error code indicating that the capability is not supported is returned.

- When the vehicle is not in P (Park) gear, the status field returns an invalid value by default.

### How to Develop

1. Import the required module.

   <!-- @[carAwareness_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { carAwareness } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Register the refueling status callback.

   <!-- @[refueling_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function subscribeRefueling(onUpdate: (data: string) => void): void {
     try {
       carAwareness.onRefueling((refuelingInfo: carAwareness.RefuelingInfo) => {
         const statusType: string = getRefuelingStatusType(refuelingInfo.status);
         hilog.info(DOMAIN, TAG, 'Refueling status: %{public}d', refuelingInfo.status);
         onUpdate(statusType);
       });
       hilog.info(DOMAIN, TAG, 'Succeeded in subscribing refueling status.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to subscribe refueling status, error code: %{public}d', err.code);
     }
   }
   ```

3. Unsubscribe from refueling status.

   <!-- @[refueling_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/CarAwareness/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   function unsubscribeRefueling(): void {
     try {
       carAwareness.offRefueling();
       hilog.info(DOMAIN, TAG, 'Succeeded in unsubscribing refueling status.');
     } catch (error) {
       const err: BusinessError = error as BusinessError;
       hilog.error(DOMAIN, TAG, 'Failed to unsubscribe refueling status, error code: %{public}d', err.code);
     }
   }
   ```

<!--no_check-->
