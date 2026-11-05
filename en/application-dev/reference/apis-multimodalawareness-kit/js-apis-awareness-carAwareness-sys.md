# @ohos.multimodalAwareness.carAwareness (Car Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @ultimate_lin-->
<!--Designer: @charlie3wx-->
<!--Tester: @fhzs-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=24b4df4dc27495886e9363f251875137a29942b4 translatedAt=2026-11-03T05:57:00.356Z pushedAt=2026-11-03T12:08:25.575Z nl=1 -->

This module provides system-level vehicle awareness capabilities, including pointing recognition, gesture recognition, and vehicle state awareness.

**Since:** 26.0.1

> **NOTE**
> 
> This page contains only the system APIs of this module. For other public APIs, see [@ohos.multimodalAwareness.carAwareness (Vehicle Awareness)](js-apis-awareness-carAwareness.md).

## Importing Modules

```ts
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## Capability

Enumerates the capability types supported by vehicle awareness.

**Since:** 26.0.1

**Model Constraint:** This API can be used only in the stage model.

**System API:** This is a system API.

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Value | Description |
| ---- | ---- | ---- |
| SPATIAL_POINT | 'SpatialPoint' | Pointing recognition capability, which supports recognizing the in-vehicle components pointed to by the user. |
| SPATIAL_GESTURE | 'SpatialGesture' | Gesture awareness capability, which supports recognizing specific user gestures. |
| CAR_STATUS | 'CarStatus' | Vehicle status awareness capability, which supports obtaining vehicle-related status information. |
| HABIT_RECOMMENDATION | 'HabitRecommendation' | Habit recommendation awareness capability, which supports generating recommendations based on user habits. |
| SPATIAL_DRAW | 'SpatialDraw' | Spatial drawing capability, which supports recognizing the user's mid-air drawing gestures. |
| GESTURE_CLOSEDOOR | 'GestureCloseDoor' | Hand-wave door-closing recognition capability, which supports recognizing the user's hand gesture for closing the door. |
| OCCUPANT_SENSE | 'OccupantSense' | Occupant awareness capability, which supports recognizing the layout and classification of occupants in the vehicle. |

## CarAwarenessInfo

Defines the general result information interface for vehicle awareness.

**Since:** 26.0.1

**Model Constraint:** This interface can be used only in the stage model.

**System API:** This is a system API.

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read-only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| timestamp | number | No | No | Timestamp of the recognition result.<br>Unit: ms. |
| capability | [Capability](#capability) | No | No | Specified awareness capability type. |
| awarenessEvent | Record\<string, Object\> | No | Yes | Key-value pairs of the awareness result data. Different capabilities return different fields. |

## CarAwarenessOptions

Defines the subscription configuration options interface for vehicle awareness.

**Since:** 26.0.1

**Model constraint:** This interface can be used only in the stage model.

**System API:** This interface is a system API.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

| Name | Type | Read-only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| parameters | Record\<string, Object\> | No | Yes | Custom awareness parameter key-value pairs, used to pass configuration items for a specific capability. |

## carAwareness.onCarAwareness

onCarAwareness(capability: Capability, callback: Callback<CarAwarenessInfo[]>, options?: CarAwarenessOptions): void

Subscribes to the vehicle awareness result. If the device does not support the capability, error code 34000002 is thrown. You can call getAllCapabilityList to query the capabilities available on the device. The data is returned asynchronously through the callback.

**Since:** 26.0.1

**Model Constraint:** This API can be used only in the stage model.

**System API:** This is a system API.

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Type of the awareness capability to subscribe to. |
| callback | Callback\<CarAwarenessInfo[]\> | Yes | Callback invoked to return the awareness result data array. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration options for the awareness capability. |

**Error Codes**

For details about the following error codes, see [Vehicle Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**

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

Unsubscribes from the vehicle awareness result of the specified type.

**Since:** 26.0.1

**Model Constraint:** This API can be used only in the stage model.

**System API:** This is a system API.

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Type of the awareness capability to unsubscribe from. |
| callback | Callback\<CarAwarenessInfo[]\> | No | Callback function. If a specific callback is passed in, the corresponding listener is unregistered; otherwise, all listeners are unregistered. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration options of the awareness capability. |

**Error Code**

For details about the following error codes, see [Vehicle Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 34000001 | Service exception. |

**Example**

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

Updates the enable/disable status of spatial action awareness.

**Since:** 26.0.1

**Model Constraint:** This API can be used only in the stage model.

**System API:** This API is a system API.

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| event | number | Yes | Enable/disable status value.<br>0: end<br>1: start<br>The value must be an integer. |

**Error Code**

For details about the following error codes, see [Vehicle Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**

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

Updates the sound zone information for spatial action awareness.

**Since:** 26.0.1

**Model constraint:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.vehicle.MMA_SPATIALACTION

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| zone | number | Yes | Sound zone ID.<br>3: rear left<br>4: rear right<br>The value must be an integer. |

**Error Codes**

For details about the error codes, see [Vehicle Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**

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

Obtains the vehicle awareness result of the specified type once.

**Since:** 26.0.1

**Model Constraint:** This API can be used only in the stage model.

**System API:** This is a system API.

**System Capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| capability | [Capability](#capability) | Yes | Type of the awareness capability to obtain. |
| options | [CarAwarenessOptions](#carawarenessoptions) | No | Optional configuration options of the awareness capability. |

**Return value**

| Type | Description |
| ---- | ---- |
| Promise\<CarAwarenessInfo[]\> | Promise used to return the array of awareness result data. |

**Error Codes**

For details about the following error codes, see [Vehicle Awareness Error Codes](errorcode-carAwareness.md).

| Error Code ID | Error Message |
| ---- | ---- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 34000001 | Service exception. |
| 34000002 | Specific capability not supported. |

**Example**

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