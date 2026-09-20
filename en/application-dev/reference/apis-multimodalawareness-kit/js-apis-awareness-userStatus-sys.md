# @ohos.multimodalAwareness.userStatus (User Status Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=cc86dfabb45b0518451eb8b3c6fe83b3414b6a7f translatedAt=2026-09-14T02:20:49.788Z pushedAt=2026-09-14T10:03:33.584Z -->

This module provides user status awareness capabilities, including user gesture recognition, face pose recognition, hand-eye coordination detection, user blowing status detection, user emotion detection, and user ambient sound detection. It is suitable for scenarios that require sensing user status to optimize the interactive experience, and helps applications provide a more natural and personalized user experience. The module adopts a subscription/callback mechanism and implements user status detection through three stages: underlying sensor data collection, feature extraction, and status determination. Developers can subscribe to the corresponding detection features based on business requirements.

**Since:** 26.0.0

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

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| deviceId | string | No | No | Device ID. A unique device identifier used to identify and distinguish different devices. The string length ranges from 0 to 64.        |
| networkId | string | No | No | Device network ID. A unique network identifier used for device networking and cross-device communication. The string length ranges from 0 to 64.      |
| deviceName | string | No | No | Device name. A user-defined device display name used to show device information in the UI. The string length ranges from 0 to 64. |
| deviceType | [DeviceType](#devicetype) | No | No | Device type. |

## UserStatusFeature

Defines the user status detection feature.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Value | Description |
| --- | --- | --- |
| GESTURES_RECOGNITION | 5 | User gesture recognition function (100 ms report interval). |
| ANTI_MISTOUCH | 6 | Anti-mistouch detection. |
| QUICK_GESTURES_RECOGNITION | 7 | User quick gesture recognition function (20 ms report interval). |
| FACE_RELATIVE_POSITION_RECOGNITION | 8 | Face relative position recognition (reporting interval: 100 ms). |
| QUICK_FACE_RELATIVE_POSITION_RECOGNITION | 9 | Quick face relative position recognition (reporting interval: 20 ms). |
| HAND_GAZE_COORDINATION | 11 | Hand-gaze coordination detection. |
| USER_BLOWING_STATUS | 12 | User blowing status detection. |
| USER_MOOD | 13 | User mood detection. |
| COMFORT_REMINDER | 15 | Ringtone comfort detection. |
| ENV_SOUND | 17 | Environment sound detection function. |
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
| ENV_SOUND | 13 | Users environment sound intensity. |
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

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| feature | [UserStatusFeature](#userstatusfeature) | Yes | No | User status detection feature. |
| status | string | Yes | No | Multi-stage detection status under a specific function. The string value indicates the corresponding detection status, and the maximum length of the string is 64. |
| result | number | Yes | No | User status detection result. **0** indicates success, and a non-zero value indicates failure. |
| errCode | number | Yes | No | Service error code. **0** indicates success, and a non-zero value indicates failure. |

## UserBlowData

Defines user blow data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| facePosition | number[] | Yes | Yes | Coordinates of the face relative to the screen. The array length is 8, representing the x and y coordinates of the four vertices (top, bottom, left, and right). The value range in the normalized coordinate system is [0,640]. Unit: px |
| strengthLevel | number | Yes | Yes | Blowing strength. The value range is [1,12].                                                 |
| blowDirection | number | Yes | Yes | Blowing direction. The value range is [0,2]. **0**: not blowing, **1**: bottom microphone, **2**: top microphone.                            |
| emotion | number | Yes | Yes | User emotion level. The value range is [0,5]. **0**: very pleasant, **1**: slightly pleasant, **2**: calm, **3**: slightly unpleasant, **4**: very angry, **5**: crying.           |
| isGazeStatus | boolean | Yes | Yes | Whether the user is gazing at the screen. The value range is [true,false].                                       |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current state. The array length is 3, representing the acceleration components in the x, y, and z directions. Unit: m/s².                |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current state. A two-dimensional array. The outer layer represents sampling at multiple points, and the inner layer is an array of length 3, representing the acceleration components in the x, y, and z directions. Unit: m/s².      |

## UserEmotionData

Defines user emotion data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| emotionRealTime | number | Yes | Yes | Real-time emotion level of the user. Value range: [0,5]. **0**: Very Pleasant, **1**: Slightly Pleasant, **2**: Calm, **3**: Slightly Unpleasant, **4**: Very Angry, **5**: Crying.  |
| confidence | number | Yes | Yes | Confidence percentage of the user's emotion. Value range: [0,100].                                  |
| isRealTime | boolean | Yes | Yes | Whether the emotion data is real-time data. Value range: [true,false].                             |
| emotionNonRealTime | number[] | Yes | Yes | Non-real-time emotion level of the user. The array contains multiple emotion values collected over a period of time, and each element has a value range of [0,5]. **0**: Very Pleasant, **1**: Slightly Pleasant, **2**: Calm, **3**: Slightly Unpleasant, **4**: Very Angry, 5: Crying. |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current state. The array length is 3, representing the acceleration components in the x, y, and z directions respectively, in m/s².                                    |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current state. It is a two-dimensional array. The outer layer represents sampling at multiple points, and the inner layer is an array of length 3, representing the acceleration components in the x, y, and z directions respectively, in m/s².      |

## ComfortReminderData

Defines comfort reminder data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level after comprehensive detection. |
| swingReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level when gazing at the screen. |
| eventType | number | Yes | No | Event type. The value **0** indicates a gaze event, and **1** indicates an ambient sound event. |

## UserFacesData

Represents data related to the user facing the screen. It inherits from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| visualAngle | number[] | Yes | Yes | Viewing angle of the user looking at the screen. Value range: [0, 90]. Unit: deg.                                            |
| angularVelocity | number[] | Yes | Yes | Angular velocity of the device in the current state. The array length is 3, representing the angular velocity components of rotation around the x, y, and z axes respectively. Unit: rad/s.                     |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current state. The array length is 3, representing the acceleration components in the x, y, and z directions respectively. Unit: m/s².                      |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current state. Two-dimensional array. The outer layer represents sampling at multiple points, and the inner layer is an array of length 3, representing the acceleration components in the x, y, and z directions respectively. Unit: m/s². |
| azimuth | number[] | Yes | Yes | Azimuth of the device in the current state. The array length is 3, representing the yaw angle (around the y-axis), pitch angle (around the x-axis), and roll angle (around the z-axis) respectively. Value range: [0, 360]. Unit: deg.  |
| faceNum | number | Yes | Yes | Number of detected faces. Value range: [0, 3].                                                    |

## UserGesturesData

Defines user gesture data, inherited from [UserFacesData](#userfacesdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | Yes | Yes | Whether the user's hand exists. Value range: [true, false].                                       |
| handPosition | number[] | Yes | Yes | Coordinate position of the hand relative to the screen. The array length is 8, representing the x and y coordinates of the four vertices (top, bottom, left, and right). The value range in the normalized coordinate system is [0, 640]. |
| motionGesture | number | Yes | Yes | User's dynamic gesture type. Value range: [0, 3]. **0**: flip up, **1**: flip down, **2**: grab screen, **3**: release.                         |
| handType | number | Yes | Yes | User's static gesture type. Value range: [0, 3]. **0**: palm, **1**: fist, **2**: scissors, **3**: heart.                         |
| directionAngle | number[] | Yes | Yes | Angle between the user's gesture and the screen direction. The array contains the angle values of the gesture in multiple dimensions. The value range of each element is [0, 90]. Unit: deg.             |
| gestureSpeed | number[] | Yes | Yes | Gesture speed. The array length is 2. The first element indicates the speed value, and the second element is a reserved bit (fixed at 0). Unit: frames per second.                           |

## UserFaceAngleData

Defines the user face angle data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | Yes | No | Network ID of the device that the user is facing. The string length ranges from 0 to 128. |

## userStatus.subscribe

subscribe(featureId: UserStatusFeature, callback: Callback&lt;UserStatusData&gt;, deviceInfo?: DeviceInfo[]): number

Subscribes to user status monitoring to obtain user status data. After calling **subscribe()**, you must call **unsubscribe()** to cancel the subscription and release callback resources when they are no longer needed. Failure to call **unsubscribe()** causes callback resource leakage and affects application performance. It is recommended to call **configure()** to configure feature parameters before calling **subscribe()** to start the subscription.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User status detection feature. |
| callback | Callback<[UserStatusData](#userstatusdata)> | Yes | Callback invoked to return the user status data. It is invoked when the subscribed user status data is updated. |
| deviceInfo | [DeviceInfo](#deviceinfo)[] | No | List of devices for which user status monitoring is to be enabled. When **featureId** is **HAND_GAZE_COORDINATION**, valid and non-empty **deviceInfo** must be provided; otherwise, the function may not work properly. For other **featureId** values, this parameter can be omitted. If an empty value, **undefined**, or null is passed, it is considered that no actual value is provided. |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Registered callback ID, which uniquely identifies the corresponding callback. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [User Status Awareness Error Codes](../errorcode-universal.md).

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
  console.error(`subscribe failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.unsubscribe

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): number

Unsubscribes from user status monitoring. This method is used in pair with **subscribe()** to cancel the subscription callback and release resources. It must be called after **subscribe()**. Unsubscribing from a **featureId** that is not subscribed returns a failure. It is recommended to call **unsubscribe()** when the application exits or no longer needs monitoring.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User Status Detection function type to unsubscribe from. Corresponds to the featureId value passed in subscribe. |
| callback | Callback<[UserStatusData](#userstatusdata)> | No | Callback for the notification event. If null, **undefined**, or **null** is passed, all notification events subscribed to by **featureId** are unsubscribed. |

**Return value**

| Type                          | Description                                                        |
| ----------------------------- | ------------------------------------------------------------------ |
| number | Returns the execution result. **0** indicates success, and a non-zero value indicates failure. |


**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [User Status Awareness Error Codes](../errorcode-universal.md).

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

try {
  let mistouchFeatureId = userStatus.UserStatusFeature.ANTI_MISTOUCH;
  userStatus.unsubscribe(mistouchFeatureId);
} catch (err) {
  let error = err as BusinessError;
  console.error(`unsubscribe failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.configure

configure(featureId: UserStatusFeature, detail: string): number

Configures feature parameters. After a successful call, the configuration parameters of the specified feature are updated, affecting the subsequent detection behavior of the feature, such as detection sensitivity, sampling frequency, and enabled detection items. It is recommended to call **configure()** to configure feature parameters before **subscribe()** to ensure that the configuration takes effect upon subscription. For features that require specific configuration (such as the real-time/non-real-time mode of **USER_MOOD**), it is recommended to call **configure()** before **subscribe()**.

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | Yes | User status detection feature to configure. |
| detail | string | Yes | Configuration parameter, a JSON format string. It contains a **params** array, where each parameter contains the **description** (parameter name) and **value** (parameter value array) fields. For the specific format and value range, see the **detail** definition table below. |

**detail Definition**

| featureId | description | value | Description |
| --- | --- | --- | --- |
| USER_MOOD | isRealTime | [ ] | **isRealTime** takes the value **0** or **1**, where **0** indicates non-real-time and **1** indicates real-time. Obtaining data in real-time mode increases performance overhead. It is recommended to select an appropriate mode based on business needs to optimize performance. |
| - | atomicCapabilities | [ ] | **atomicCapabilities** can contain one or more values, and duplicate values are automatically deduplicated. Enabling multiple capabilities increases the computational load. It is recommended to select capabilities on demand based on business requirements to optimize performance.<br>5=atomic gravity sensor<br>8=atomic linear acceleration sensor<br>12=atomic emotion capability |
| GESTURES_RECOGNITION<br>QUICK_GESTURES_RECOGNITION | dynamicGestureTypes | [ ] | **dynamicGestureTypes** can contain one or more values, and duplicate values are invalid. Enabling multiple gesture types increases the recognition computational load. It is recommended to select them on demand to optimize performance.<br>0=grab<br>1=swipe down<br>2=initial flip-up gesture<br>3=initial flip-down gesture<br>4=swipe up<br>5=fist to open palm<br>6=disappear |
| - | staticGestureTypes | [ ] | **staticGestureTypes** can contain one or more values, and duplicate values are invalid. Enabling multiple gesture types increases the recognition computational load. It is recommended to select them on demand to optimize performance.<br>7=palm<br>8=scissors hand<br>9=fist<br>10=heart gesture |
| USER_BLOWING_STATUS | atomicCapabilities | [ ] | **atomicCapabilities** can contain one or more values, and duplicate values are automatically deduplicated. Enabling multiple capabilities increases the computational load. It is recommended to select capabilities on demand based on business requirements to optimize performance.<br>5=atomic gravity sensor<br>8=atomic linear acceleration sensor<br>11=atomic blowing capability<br>12=atomic emotion capability<br>15=atomic screen gaze capability |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Configuration execution result. The value **0** indicates that the operation is successful, and a non-zero value indicates that the operation fails. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [User Status Awareness Error Codes](../errorcode-universal.md).

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
  console.info('configure result: ', result);
} catch (err) {
  let error = err as BusinessError;
  console.error(`configure failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.queryCapabilities

queryCapabilities(capabilities: UserStatusAtomicCap[]): UserStatusAtomicCap[]

Queries the atomic capabilities supported by the device. This method determines whether the specified atomic capabilities are supported through the underlying interface and returns the list of capabilities actually supported by the device.

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

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [User Status Awareness Error Codes](../errorcode-universal.md).

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
  console.info('Query capabilities result: ', result);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Query capabilities failed. Code: ${error.code}, message: ${error.message}`);
}
```
