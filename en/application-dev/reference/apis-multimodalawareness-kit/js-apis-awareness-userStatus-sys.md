# @ohos.multimodalAwareness.userStatus (User Status Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b1f735a868479d304c89ba93e36d0563076a2e85 translatedAt=2026-11-04T02:30:11.781Z pushedAt=2026-11-04T03:24:28.576Z nl=1 -->

This module provides user status awareness capabilities, including gesture detection and ambient sound detection.

**Since**: 26.0.0

> **NOTE**
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## DeviceType

Defines the device type.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| UNKNOWN_TYPE | 0 | Unknown type. |
| PC | 0x0C | PC. |
| PHONE | 0x0E | Phone. |
| TABLET | 0x11 | Tablet. |

## DeviceInfo

Defines device information.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| deviceId | string | No | No | Indicates the device ID. String length range [0,64]. |
| networkId | string | No | No | Indicates the device network ID. String length range [0,64]. |
| deviceName | string | No | No | Indicates the device name. String length range [0,64]. |
| deviceType | [DeviceType](#devicetype) | No | No | Device type. |

## UserStatusFeature

Defines the user status detection feature.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| GESTURES_RECOGNITION | 5 | Gesture recognition (reporting interval: 100 ms). |
| ANTI_MISTOUCH | 6 | Anti-mistouch detection. |
| QUICK_GESTURES_RECOGNITION | 7 | Quick gesture recognition (reporting interval: 20 ms). |
| FACE_RELATIVE_POSITION_RECOGNITION | 8 | Face relative position recognition (reporting interval: 100 ms). |
| QUICK_FACE_RELATIVE_POSITION_RECOGNITION | 9 | Quick face relative position recognition (reporting interval: 20 ms). |
| HAND_GAZE_COORDINATION | 11 | Hand-gaze coordination detection. |
| USER_BLOWING_STATUS | 12 | User blowing status detection. |
| USER_MOOD | 13 | User mood detection. |
| COMFORT_REMINDER | 15 | Ringtone comfort detection. |
| ENV_SOUND | 17 | Environmental sound detection. |
| EXT_SCREEN_ANTI_MISTOUCH | 19 | External screen anti-mistouch detection. |

## UserStatusAtomicCap

Defines the atomic service capabilities supported by user status.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| ATOMIC_UNKNOWN | 0 | Unknown atomic service capability. |
| FACE_RELATIVE_POSITION | 1 | Detection of face relative position to screen. |
| FACE_NUM_CHANGE | 2 | Face number change detection. |
| GESTURE | 3 | User gesture detection. |
| FACE_ANGLE | 4 | Detection of face angle relative to screen. |
| SENSOR_GRAVITY | 5 | Sensor gravity data detection. |
| SENSOR_GYROSCOPE | 6 | Sensor gyroscope data detection. |
| SENSOR_ACCELEROMETER | 7 | Sensor accelerometer data detection. |
| SENSOR_LINEAR_ACCELERATION | 8 | Sensor linear acceleration data detection. |
| SENSOR_ROTATION_VECTOR | 9 | Sensor rotation vector data detection. |
| SENSOR_ORIENTATION | 10 | Sensor orientation data detection. |
| BLOWING_STATUS | 11 | User blowing data detection. |
| MOOD_STATUS | 12 | User mood data detection. |
| ENV_SOUND | 13 | User environment sound intensity detection. |
| NOISE_SOUND | 14 | User noise intensity detection. |
| EYE_GAZE_SCREEN | 15 | Detection of user gaze at the screen. |

## ReminderLevel

Defines the reminder intensity level, used when triggering reminder ringtones.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| WEAK_REMINDER | 0 | Weak reminder level. |
| NORMAL_REMINDER | 1 | Normal reminder level. |

## UserStatusData

Defines user status data.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| feature | [UserStatusFeature](#userstatusfeature) | Yes | No | User status detection feature. |
| status | string | Yes | No | Indicates the multi-stage detection status under a specific function. The string length ranges from 0 to 64. |
| result | number | Yes | No | User status detection result. **0** indicates success, and a non-zero value indicates failure. |
| errCode | number | Yes | No | Service error code. **0** indicates success, and a non-zero value indicates failure. |

## UserBlowData

Defines user blow data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| facePosition | number[] | Yes | Yes | Indicates the position of the face relative to the screen. Value range [0,640]. |
| strengthLevel | number | Yes | Yes | Blowing strength. The value range is [1,12]. |
| blowDirection | number | Yes | Yes | Blowing direction. The value range is [0,2]. **0**: not blowing, **1**: bottom microphone, **2**: top microphone. |
| emotion | number | Yes | Yes | User emotion level. The value range is [0,5]. **0**: very pleasant, **1**: slightly pleasant, **2**: calm, **3**: slightly unpleasant, **4**: very angry, **5**: crying. |
| isGazeStatus | boolean | Yes | Yes | Whether the user is gazing at the screen. The value range is [true,false]. |
| gravityAcceleration | number[] | Yes | Yes | Indicates the gravity acceleration of the device in the current status. Unit is m/s². |
| linearAcceleration | number[][] | Yes | Yes | Indicates the linear acceleration of the device in the current status. Unit is m/s². |

## UserEmotionData

Defines user emotion data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| emotionRealTime | number | Yes | Yes | Real-time emotion level of the user. Value range: [0,5]. **0**: Very Pleasant, **1**: Slightly Pleasant, **2**: Calm, **3**: Slightly Unpleasant, **4**: Very Angry, **5**: Crying. |
| confidence | number | Yes | Yes | Confidence percentage of the user's emotion. Value range: [0,100]. |
| isRealTime | boolean | Yes | Yes | Whether the emotion data is real-time data. Value range: [true,false]. |
| emotionNonRealTime | number[] | Yes | Yes | Non-real-time emotion level of the user. Value range: [0,5]. **0**: Very Pleasant, **1**: Slightly Pleasant, **2**: Calm, **3**: Slightly Unpleasant, **4**: Very Angry, **5**: Crying. |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current state. Unit: m/s². |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current state. Unit: m/s². |

## ComfortReminderData

Defines comfort reminder data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level after comprehensive detection. |
| swingReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level when the user is gazing at the device. |
| eventType | number | Yes | No | Event type. The value range is [0, 1]. 0: gaze event; 1: ambient sound event. |

## UserFacesData

Defines user face data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| visualAngle | number[] | Yes | Yes | Indicates the user's viewing angle of the screen. Value range: [0, 90]. |
| angularVelocity | number[] | Yes | Yes | Indicates the angular velocity of the device in the current status. Unit is rad/s. |
| gravityAcceleration | number[] | Yes | Yes | Indicates the gravity acceleration of the device in the current status. Unit is m/s². |
| linearAcceleration | number[][] | Yes | Yes | Indicates the linear acceleration of the device in the current status. Unit is m/s². |
| azimuth | number[] | Yes | Yes | Indicates the azimuth of the device in the current status. Value range: [0, 360]. |
| faceNum | number | Yes | Yes | Number of detected faces. Value range: [0, 3]. |

## UserGesturesData

Defines user gesture data, inherited from [UserFacesData](#userfacesdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | Yes | Yes | Whether the user's hand exists. Value range: [true, false]. |
| handPosition | number[] | Yes | Yes | Indicates the position of the hand relative to the screen. The value range is [0, 640]. |
| motionGesture | number | Yes | Yes | User's dynamic gesture type. Value range: [0, 3]. **0**: flip up, **1**: flip down, **2**: grab screen, **3**: release. |
| handType | number | Yes | Yes | User's static gesture type. Value range: [0, 3]. **0**: palm, **1**: fist, **2**: scissors, **3**: heart. |
| directionAngle | number[] | Yes | Yes | Indicates the angle between the user's gesture and the screen direction. The value range is [0, 90]. |
| gestureSpeed | number[] | Yes | Yes | Indicates the gesture speed. The unit is frames per second. |

## UserFaceAngleData

Defines the user face angle data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | Required | No | Network ID of the device that the user is facing. The string length ranges from 0 to 128. |

## userStatus.subscribe

subscribe(featureId: UserStatusFeature, callback: Callback&lt;UserStatusData&gt;, deviceInfo?: DeviceInfo[]): number

Subscribes to user status monitoring to obtain user status data.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User status detection feature. |
| callback | Callback<[UserStatusData](#userstatusdata)> | Yes | Callback used to return the user status data. |
| deviceInfo | [DeviceInfo](#deviceinfo)[] | No | List of devices for which user status monitoring is to be enabled. When featureId is HAND_GAZE_COORDINATION, the actual deviceInfo information must be provided. If an empty value, undefined, or null is passed, it is considered that no actual value is provided. |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Registered callback ID, which uniquely identifies the corresponding callback. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userStatus } from '@kit.MultimodalAwarenessKit';

const TAG = 'UserStatusDemo';
try {
  let mistouchFeatureId = userStatus.UserStatusFeature.ANTI_MISTOUCH;
  userStatus.subscribe(mistouchFeatureId, (data: userStatus.UserStatusData) => {
    console.info(TAG, 'subscribe succeeded, result: ' + data.result);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error("subscribe failed, err code is " + error.code);
}
```

## userStatus.unsubscribe

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): number

Unsubscribes from user status monitoring.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User status detection feature. |
| callback | Callback<[UserStatusData](#userstatusdata)> | No | Callback for the notification event. If null, **undefined**, or **null** is passed, all notification events subscribed to by **featureId** are unsubscribed. |

**Return value**

| Type                          | Description                                                        |
| ----------------------------- | ------------------------------------------------------------------ |
| number | Returns the execution result. **0** indicates success, and a non-zero value indicates failure. |


**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900003 | Unsubscription failed. Possible causes: <br>1. Callback failure. <br>2. Node-API invocation exception, such as invalid Node-API status. <br>3. IPC request exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userStatus } from '@kit.MultimodalAwarenessKit';

const TAG = 'UserStatusDemo';
try {
  let mistouchFeatureId = userStatus.UserStatusFeature.ANTI_MISTOUCH;
  userStatus.unsubscribe(mistouchFeatureId, (data: userStatus.UserStatusData) => {
    console.info(TAG, `unsubscribe succeeded, result: ${data.result}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error("unsubscribe failed, err code is " + error.code);
}
```

## userStatus.configure

configure(featureId: UserStatusFeature, detail: string): number

Configures feature parameters.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User status detection feature to configure. |
| detail | string | Yes | Detailed configuration parameters in JSON format. |

**detail Definition**

| featureId | description | value | Description |
| --- | --- | --- | --- |
| USER_MOOD | isRealTime | [ ] | The value of isRealTime is 0 or 1, where 0 indicates non-real-time and 1 indicates real-time. |
| - | atomicCapabilities | [ ] | The value of atomicCapabilities can contain at least one or more values, and duplicate values are invalid.<br>5 = atomic gravity sensor<br>8 = atomic linear acceleration sensor<br>12 = atomic emotion capability |
| GESTURES_RECOGNITION<br>QUICK_GESTURES_RECOGNITION | dynamicGestureTypes | [ ] | The value of dynamicGestureTypes can contain at least one or more values, and duplicate values are invalid.<br>"fetch" = fetch<br>"slide_up" = slide up<br>"slide_down" = slide down<br>"start_up" = flip-up initial gesture<br>"start_down" = flip-down initial gesture<br>"fist_to_palm" = fist to palm<br>"disappear" = disappear |
| - | staticGestureTypes | [ ] | The value of staticGestureTypes can contain at least one or more values, and duplicate values are invalid.<br>"palm" = palm<br>"fingerV" = scissors hand<br>"fist" = fist<br>"heartGesture" = heart gesture |
| USER_BLOWING_STATUS | atomicCapabilities | [ ] | The value of atomicCapabilities can contain at least one or more values, and duplicate values are invalid.<br>5 = atomic gravity sensor<br>8 = atomic linear acceleration sensor<br>11 = atomic blowing capability<br>12 = atomic emotion capability<br>15 = atomic screen gaze capability |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Configuration execution result. The value **0** indicates that the operation is successful, and a non-zero value indicates that the operation fails. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userStatus } from '@kit.MultimodalAwarenessKit';

interface ConfigParam {
  description: string;
  value: number[];
}
interface ConfigDetail {
  params: ConfigParam[];
}
const moodFeatureId = userStatus.UserStatusFeature.USER_MOOD;
const configData: ConfigDetail = {
  params: [
    { description: "isRealTime", value: [1] },
    { description: "atomicCapabilities", value: [5] }
  ]
};
try {
  const result = userStatus.configure(moodFeatureId, JSON.stringify(configData));
  console.info("configure result: ", result);
} catch (err) {
  let error = err as BusinessError;
  console.error("configure failed, err code is " + error.code);
}
```

## userStatus.queryCapabilities

queryCapabilities(capabilities: UserStatusAtomicCap[]): UserStatusAtomicCap[]

Queries the atomic service capabilities supported by the device.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](#userstatusatomiccap)[] | Yes | List of atomic service capabilities to query. |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| [UserStatusAtomicCap](#userstatusatomiccap)[]| List of atomic service capabilities supported by the device. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { userStatus } from '@kit.MultimodalAwarenessKit';

try {
  const capabilities: userStatus.UserStatusAtomicCap[] = [
    userStatus.UserStatusAtomicCap.SENSOR_GRAVITY,
    userStatus.UserStatusAtomicCap.SENSOR_GYROSCOPE
  ];
  const result = userStatus.queryCapabilities(capabilities);
  console.info("Query capabilities result: ", result);
} catch (err) {
  let error = err as BusinessError;
  console.error("Query capabilities failed, err code is " + error.code);
}
```
