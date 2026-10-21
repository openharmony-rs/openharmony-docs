# @ohos.multimodalAwareness.carAwareness (Car Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=561a48f0279b682322ad16aa122a3161b679e716 translatedAt=2026-09-14T01:47:38.457Z pushedAt=2026-09-14T10:03:33.569Z -->

This module provides car awareness capabilities, including spatial motion interaction, real-time weather recognition, and refueling status recognition.

**Since:** 26.0.1

## Modules to Import

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## Capability

Enumerates the capability types supported by car awareness.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Value | Description |
| ---- | ---- | ---- |
| SPATIAL_MOTION | 'SpatialMotion' | Spatial motion capability, which supports recognizing the user's air gestures for operating the screen. |
| SPATIAL_POINT | 'SpatialPoint' | Spatial point capability, which supports recognizing the in-car components pointed to by the user.<br>**System API:** This enum member is a system API. |
| SPATIAL_GESTURE | 'SpatialGesture' | Spatial gesture capability, which supports recognizing the user's specific postures and actions.<br>**System API:** This enum member is a system API. |
| REALTIME_WEATHER | 'RealTimeWeather' | Real-time weather capability, which supports recognizing the weather conditions of the environment where the car is currently located. |
| REFUELING | 'Refueling' | Refueling capability, which supports recognizing the start and end states of car refueling. |
| CAR_STATUS | 'CarStatus' | Car status capability, which supports obtaining vehicle-related status information.<br>**System API:** This enum member is a system API. |
| HABIT_RECOMMENDATION | 'HabitRecommendation' | Habit recommendation capability, which supports generating recommendations based on user habits.<br>**System API:** This enum member is a system API. |
| SPATIAL_DRAW | 'SpatialDraw' | Spatial draw capability, which supports identifying the users' air gestures during mid-air drawing.<br>**System API:** This enum member is a system API. |
| GESTURE_CLOSEDOOR | 'GestureCloseDoor' | Gesture close door capability, which supports recognizing user's hand action for closing the doors.<br>**System API:** This enum member is a system API. |
| OCCUPANT_SENSE | 'OccupantSense' | Occupant sense capability, which supports recognizing position and classification of in-car occupants.<br>**System API:** This enum member is a system API. |

## SpatialMotionInfo

Interface for spatial motion response info.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | No | No | Timestamp of the recognition result.<br>Unit: ms. |
| pointX | number | No | No | X-axis coordinate of the hand on the screen. |
| pointY | number | No | No | Y-axis coordinate of the hand on the screen. |
| event | number | No | No | Gesture event type.<br>**-1**: invalid<br>**0**: ready<br>**1**: move<br>**2**: tap |

## carAwareness.onSpatialMotion

onSpatialMotion(callback: Callback\<SpatialMotionInfo\>): void

Subscribes to spatial motion awareness results. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permission:** ohos.permission.vehicle.MMA_SPATIALACTION

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | Yes | Callback invoked to return the spatial motion awareness data. |

**Error codes**

For details about the error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onSpatialMotion((data) => {
    hilog.info(DOMAIN, TAG, 'Spatial motion event: %{public}d', data.event);
    hilog.info(DOMAIN, TAG, 'Point coordinate: (%{public}d, %{public}d)', data.pointX, data.pointY);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe spatial motion failed, error code: %{public}d', e.code);
}
```

## carAwareness.offSpatialMotion

offSpatialMotion(callback?: Callback\<SpatialMotionInfo\>): void

Unsubscribes from spatial motion results.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission:** ohos.permission.vehicle.MMA_SPATIALACTION

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | No | Callback for spatial motion event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |

**Error Codes**

For details about the error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

// Unsubscribe the specified listener.
let motionCallback = (motionInfo : carAwareness.SpatialMotionInfo) => {
  hilog.info(DOMAIN, TAG, 'Spatial motion data received');
};

try {
  carAwareness.offSpatialMotion(motionCallback);
  hilog.info(DOMAIN, TAG, 'Unsubscribe spatial motion succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe spatial motion failed, error code: %{public}d', e.code);
}

// Unsubscribe all listeners.
try {
  carAwareness.offSpatialMotion();
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe all spatial motion failed, error code: %{public}d', e.code);
}
```

## RealTimeWeatherInfo

Interface for real-time weather response info.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | No | No | Timestamp of the recognition result.<br>Unit: ms. |
| weather | number | No | No | Weather status.<br>-1: Invalid<br>0: Other<br>1: Fog<br>2: Dense fog<br>3: Snow<br>4: Heavy snow<br>5: Rain<br>6: Heavy rain |

## carAwareness.onRealTimeWeather

onRealTimeWeather(callback: Callback\<RealTimeWeatherInfo\>): void

Subscribes to real-time weather awareness results. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permission:** ohos.permission.vehicle.MMA_WEATHER

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RealTimeWeatherInfo\> | Yes | Callback invoked to return the real-time weather awareness data. |

**Error codes**

For details about the error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onRealTimeWeather((data) => {
    hilog.info(DOMAIN, TAG, 'Current weather status: %{public}d', data.weather);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe realtime weather failed, error code: %{public}d', e.code);
}
```

## carAwareness.offRealTimeWeather

offRealTimeWeather(callback?: Callback\<RealTimeWeatherInfo\>): void

Unsubscribes from real-time weather results.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permission:** ohos.permission.vehicle.MMA_WEATHER

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RealTimeWeatherInfo\> | No | Callback for the real-time weather event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |

**Error codes**

For details about the error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.offRealTimeWeather();
  hilog.info(DOMAIN, TAG, 'Unsubscribe realtime weather succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe realtime weather failed, error code: %{public}d', e.code);
}
```

## RefuelingInfo

Interface for refueling response info.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | No | No | Timestamp of the recognition result.<br>Unit: ms. |
| status | number | No | No | Refueling status.<br>-1: invalid<br>0: idle (refueling is not started)<br>1: refueling started<br>2: refueling finished |

## carAwareness.onRefueling

onRefueling(callback: Callback\<RefuelingInfo\>): void

Subscribes to the refueling status awareness result. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**Required permission:** ohos.permission.vehicle.MMA_ENERGYREFILL

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RefuelingInfo\> | Yes | Callback invoked to return the refueling recognition data. |

**Error codes**

For details about the error codes, see [Car Awareness error codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.onRefueling((data) => {
    hilog.info(DOMAIN, TAG, 'Refueling status: %{public}d', data.status);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe refueling failed, error code: %{public}d', e.code);
}
```

## carAwareness.offRefueling

offRefueling(callback?: Callback\<RefuelingInfo\>): void

Unsubscribes from the refueling status result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**Required permission:** ohos.permission.vehicle.MMA_ENERGYREFILL

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RefuelingInfo\> | No | Callback for the refueling status event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |

**Error codes**

For details about the error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 34000001 | Service exception. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

try {
  carAwareness.offRefueling();
  hilog.info(DOMAIN, TAG, 'Unsubscribe refueling succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe refueling failed, error code: %{public}d', e.code);
}
```

## carAwareness.getAllCapabilityList

getAllCapabilityList(): Promise&lt;Capability[]&gt;

Obtains the list of all car awareness capabilities supported by the current device.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Returns**

| Type | Description |
| ---- | ---- |
| Promise\<Capability[]\> | Promise used to return the list of awareness capability enums supported by the device. |

**Error code:**

For details about the following error codes, see [Car Awareness Error Code](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

carAwareness.getAllCapabilityList()
  .then((list) => {
    hilog.info(DOMAIN, TAG, 'Supported capability list: %{public}s', JSON.stringify(list));
  })
  .catch((err: BusinessError) => {
    hilog.error(DOMAIN, TAG, 'Get capability list failed, error code: %{public}d', err.code);
  });
```