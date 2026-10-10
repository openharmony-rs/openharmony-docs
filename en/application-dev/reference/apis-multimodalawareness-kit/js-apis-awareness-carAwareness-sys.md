# @ohos.multimodalAwareness.carAwareness (Car Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=561a48f0279b682322ad16aa122a3161b679e716 translatedAt=2026-09-14T01:43:01.196Z pushedAt=2026-09-14T10:03:33.568Z -->

This module provides system-level car awareness capabilities, including spatial point, spatial motion, and car status awareness.

**Since:** 26.0.1

> **NOTE**
> 
> This page contains only the system APIs of this module. For other public APIs, see [@ohos.multimodalAwareness.carAwareness (Car Awareness)](js-apis-awareness-carAwareness.md).

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

## CarAwarenessInfo

Interface for general car awareness response info.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | No | No | Timestamp of the recognition result.<br>Unit: ms. |
| capability | [Capability](#capability) | No | No | Indicates specific awareness capability type. |
| awarenessEvent | Record\<string, Object\> | No | Yes | Key-value pair of the awareness result data. Different capabilities return different fields. |

## CarAwarenessOptions

Interface for car awareness subscription options.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| parameters | Record\<string, Object\> | No | Yes | Custom awareness parameter key-value pairs, used to pass in configuration items for a specific capability. |

## carAwareness.onCarAwareness

onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?: CarAwarenessOptions): void

Subscribes to car awareness results. If the device does not support the capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Specifies the type of the awareness capability to subscribe to. |
| callback | Callback\<CarAwarenessInfo[]\> | Yes | Callback used to return the array of awareness response data. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration items of the awareness capability. |

**Error codes**

For details about the error codes, see [Car Awareness error codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
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
  carAwareness.onCarAwareness(carAwareness.Capability.SPATIAL_POINT, (dataList: carAwareness.CarAwarenessInfo[]) => {
    hilog.info(DOMAIN, TAG, 'Car awareness data count: %{public}d', dataList.length);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Subscribe car awareness failed, error code: %{public}d', e.code);
}
```

## carAwareness.offCarAwareness

offCarAwareness(capability: Capability, callback?: Callback<CarAwarenessInfo[]>, options?: CarAwarenessOptions): void

Unsubscribes from the specific car awareness capability result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Specifies the type of the awareness capability to unsubscribe. |
| callback | Callback\<CarAwarenessInfo[]\> | No | Callback used to return specific car awareness event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration items of the awareness capability. |

**Error Codes**

For details about the following error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 34000001 | Service exception. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

let awarenessCallback = (dataList: carAwareness.CarAwarenessInfo[]) => {
  hilog.info(DOMAIN, TAG, 'Receive car awareness data');
};

try {
  carAwareness.offCarAwareness(carAwareness.Capability.SPATIAL_POINT, awarenessCallback);
  hilog.info(DOMAIN, TAG, 'Unsubscribe car awareness succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Unsubscribe car awareness failed, error code: %{public}d', e.code);
}
```

## carAwareness.updateSpatialActionEnableStatus

updateSpatialActionEnableStatus(event: number): void

Updates the start/stop status of spatial action awareness.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| event | number | Yes | Start/stop status value.<br>**0**: end<br>**1**: start<br>The value must be an integer. |

**Error codes**

For details about the following error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
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
  carAwareness.updateSpatialActionEnableStatus(1);
  hilog.info(DOMAIN, TAG, 'Enable spatial action succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Update spatial action status failed, error code: %{public}d', e.code);
}
```

## carAwareness.updateSpatialActionZone

updateSpatialActionZone(zone: number): void

Updates the voice zone information for spatial action awareness.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| zone | number | Yes | Voice zone ID.<br>**3**: rear left<br>**4**: rear right<br>The value must be an integer. |

**Error codes**

For details about the following error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
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
  carAwareness.updateSpatialActionZone(3);
  hilog.info(DOMAIN, TAG, 'Update spatial action zone succeed');
} catch (err) {
  let e: BusinessError = err as BusinessError;
  hilog.error(DOMAIN, TAG, 'Update spatial action zone failed, error code: %{public}d', e.code);
}
```

## carAwareness.getCarAwareness

getCarAwareness(capability: Capability, options?: CarAwarenessOptions): Promise<CarAwarenessInfo[]>

Obtains the car awareness result of the specified type once.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Specifies the type of the awareness capability result to obtain. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration items of the awareness capability. |

**Returns**

| Type | Description |
| ---- | ---- |
| Promise\<CarAwarenessInfo[]\> | Promise used to return an array of awareness result data. |

**Error codes**

For details about the following error codes, see [Car Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**:

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;
const TAG = 'CarAwareness';

carAwareness.getCarAwareness(carAwareness.Capability.CAR_STATUS)
  .then((dataList: carAwareness.CarAwarenessInfo[]) => {
    hilog.info(DOMAIN, TAG, 'Get car awareness data succeed');
  })
  .catch((err: BusinessError) => {
    hilog.error(DOMAIN, TAG, 'Get car awareness failed, error code: %{public}d', err.code);
  });
```