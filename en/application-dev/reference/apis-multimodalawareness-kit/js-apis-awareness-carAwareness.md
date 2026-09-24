# @ohos.multimodalAwareness.carAwareness (Car Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=561a48f0279b682322ad16aa122a3161b679e716 translatedAt=2026-09-14T01:47:38.457Z pushedAt=2026-09-14T10:03:33.569Z -->

This module provides car awareness capabilities, including air gesture interaction, real-time weather recognition, and refueling status recognition.

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
| SPATIAL_MOTION | 'SpatialMotion' | Air gesture awareness capability, which supports recognizing the user's air gestures for operating the screen. |
| SPATIAL_POINT | 'SpatialPoint' | Pointing recognition capability, which supports recognizing the in-car components pointed to by the user.<br>**System API:** This enum member is a system API. |
| SPATIAL_GESTURE | 'SpatialGesture' | Body motion awareness capability, which supports recognizing the user's specific postures and actions.<br>**System API:** This enum member is a system API. |
| REALTIME_WEATHER | 'RealTimeWeather' | Real-time weather awareness capability, which supports recognizing the weather conditions of the environment where the car is currently located. |
| REFUELING | 'Refueling' | Refueling recognition capability, which supports recognizing the start and end states of car refueling. |
| CAR_STATUS | 'CarStatus' | Car status awareness capability, which supports obtaining vehicle-related status information.<br>**System API:** This enum member is a system API. |
| CAR_CFG | 'CarCfg' | Car configuration awareness capability, which supports obtaining car configuration-related information.<br>**System API:** This enum member is a system API. |
| HABIT_RECOMMENDATION | 'HabitRecommendation' | Habit recommendation awareness capability, which supports generating recommendations based on user habits.<br>**System API:** This enum member is a system API. |

## SpatialMotionInfo

Defines the result information API for air gesture awareness.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | Yes | No | Timestamp of the recognition result.<br>Unit: ms. |
| pointX | number | Yes | No | X-axis coordinate of the hand on the screen. |
| pointY | number | Yes | No | Y-axis coordinate of the hand on the screen. |
| event | number | Yes | No | Gesture event type.<br>**-1**: invalid<br>**0**: ready<br>**1**: move<br>**2**: tap |

## carAwareness.onSpatialMotion

onSpatialMotion(callback: Callback\<SpatialMotionInfo\>): void

Enables air gesture awareness and subscribes to air gesture awareness results. If the device does not support this capability, error code 34000002 is thrown. You can call **getAllCapabilityList** to query the available capabilities of the device. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permission:** ohos.permission.vehicle.MMA_SPATIALACTION

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | Yes | Callback invoked to return the air gesture awareness data. |

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

Closes air gesture awareness and unsubscribes from air gesture results.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required Permission:** ohos.permission.vehicle.MMA_SPATIALACTION

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<SpatialMotionInfo\> | No | Callback for the air gesture event. If a specific callback is passed in, only the corresponding listener is unregistered; if no callback is passed in, all listeners are unregistered. |

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
let motionCallback = (data) => {
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

Defines the result information of real-time weather awareness.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | Yes | No | Timestamp of the recognition result.<br>Unit: ms. |
| weather | number | Yes | No | Weather status.<br>-1: Invalid<br>0: Sunny/Cloudy<br>1: Light fog<br>2: Dense fog<br>3: Light snow<br>4: Heavy snow<br>5: Light rain<br>6: Heavy rain |

## carAwareness.onRealTimeWeather

onRealTimeWeather(callback: Callback\<RealTimeWeatherInfo\>): void

Enables real-time weather awareness and subscribes to real-time weather awareness results. If the device does not support this capability, error code 34000002 is thrown. You can call **getAllCapabilityList** to query the available capabilities of the device. The data is returned asynchronously through the callback.

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

Closes real-time weather awareness and unsubscribes from real-time weather results.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Required permission:** ohos.permission.vehicle.MMA_WEATHER

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RealTimeWeatherInfo\> | No | Callback for the real-time weather event. If a specific callback is passed in, the corresponding listener is unregistered; if no callback is passed in, all listeners are unregistered. |

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

Defines the result information API for refueling recognition.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | Yes | No | Timestamp of the recognition result.<br>Unit: ms. |
| status | number | Yes | No | Refueling status.<br>-1: invalid<br>0: idle (refueling not started)<br>1: refueling started<br>2: refueling finished |

## carAwareness.onRefueling

onRefueling(callback: Callback\<RefuelingInfo\>): void

Enables refueling awareness and subscribes to the refueling status awareness result. If the device does not support this capability, error code 34000002 is thrown. You can call getAllCapabilityList to query the available capabilities of the device. The data is returned asynchronously through the callback.

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

Closes refueling awareness and unsubscribes from the refueling status result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**Required permission:** ohos.permission.vehicle.MMA_ENERGYREFILL

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| callback | Callback\<RefuelingInfo\> | No | Callback for the refueling status event. If a specific callback is passed in, the corresponding listener is unregistered; otherwise, all listeners are unregistered. |

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
| Promise\<Capability[]\> | Promise object that returns the list of awareness capability enums supported by the device. |

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