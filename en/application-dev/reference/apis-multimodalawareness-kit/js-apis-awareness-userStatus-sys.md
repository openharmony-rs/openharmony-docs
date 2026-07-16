# @ohos.multimodalAwareness.userStatus (User Status Awareness)

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @wyxpku-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=d18790e6ef1247c1fd8194f3838e7698bf6e9bf2 translatedAt=2026-06-24T06:30:34.763Z pushedAt=2026-06-25T01:35:11.440Z -->

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

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| deviceId | string | No | No | Device ID. |
| networkId | string | No | No | Device network ID. |
| deviceName | string | No | No | Device name. |
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

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| feature | [UserStatusFeature](#userstatusfeature) | Yes | No | User status detection feature. |
| status | string | Yes | No | Multi-stage detection status under a specific feature. |
| result | number | Yes | No | User status detection result. |
| errCode | number | Yes | No | Service error code. The default value 0 indicates success.|

## UserBlowData

Defines user blow data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| facePosition | number[] | Yes | Yes | Face position relative to the screen. |
| strengthLevel | number | Yes | Yes | Blowing strength. |
| blowDirection | number | Yes | Yes | Blowing direction. |
| emotion | number | Yes | Yes | User emotion level. |
| isGazeStatus | boolean | Yes | Yes | Whether the user is gazing at the screen. |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current status. |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current status. |

## UserEmotionData

Defines user emotion data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| emotionRealTime | number | Yes | Yes | User's real-time emotion level. |
| confidence | number | Yes | Yes | Confidence level of the user's emotion. |
| isRealTime | boolean | Yes | Yes | Whether the emotion data is real-time data. |
| emotionNonRealTime | number[] | Yes | Yes | User's non-real-time emotion level. |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current status. |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current status. |

## ComfortReminderData

Defines comfort reminder data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level after comprehensive detection. |
| swingReminderData | [ReminderLevel](#reminderlevel) | Yes | No | Reminder level when the user is gazing at the device. |
| eventType | number | Yes | No | Event type. |

## UserFacesData

Defines user face data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| visualAngle | number[] | Yes | Yes | Viewing angle of the user looking at the screen. |
| angularVelocity | number[] | Yes | Yes | Angular velocity of the device in the current status. |
| gravityAcceleration | number[] | Yes | Yes | Gravity acceleration of the device in the current status. |
| linearAcceleration | number[][] | Yes | Yes | Linear acceleration of the device in the current status. |
| azimuth | number[] | Yes | Yes | Azimuth of the device in the current status. |
| faceNum | number | Yes | Yes | Number of detected faces. |

## UserGesturesData

Defines user gesture data, inherited from [UserFacesData](#userfacesdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | Yes | Yes | Whether the user's hand exists. |
| handPosition | number[] | Yes | Yes | Position of the hand relative to the screen. |
| motionGesture | number | Yes | Yes | User's dynamic gesture type. |
| handType | number | Yes | Yes | User's static gesture type. |
| directionAngle | number[] | Yes | Yes | Angle between the user's gesture and the screen direction. |
| gestureSpeed | number[] | Yes | Yes | Gesture speed. |

## UserFaceAngleData

Defines the user face angle data, inherited from [UserStatusData](#userstatusdata).

**Since**: 26.0.0

**System capability**: SystemCapability.MultimodalAwareness.UserStatus

**System API**: This is a system API.

| Name | Type | Read-only | Optional | Description |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | Yes | No | Network ID of the device the user is facing. |

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
| deviceInfo | [DeviceInfo](#deviceinfo)[] | No | List of devices for which to enable user status monitoring. |

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Registered callback ID, which uniquely identifies the corresponding callback. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind native object to JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

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
| callback | Callback<[UserStatusData](#userstatusdata)> | No | Callback used to return the user status data. |

**Return value**

| Type                          | Description                                                        |
| ----------------------------- | ------------------------------------------------------------------ |
| number | Configuration execution result. The value **0** indicates that the operation is successful, and a non-zero value indicates that the operation fails. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
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

**Return value**

| Type                           | Description         |
| ---------------------------- | ---------- |
| number | Configuration execution result. The value **0** indicates that the operation is successful, and a non-zero value indicates that the operation fails. |

**Error codes**

For details about the following error codes, see [User Status Awareness Error Codes](errorcode-userStatus.md) and [General Error Codes](../errorcode-universal.md).

| ID | Error Message |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 33900001 | Service exception. Possible causes: <br>1. Invalid parameter. <br>2. Node-API invocation exception, such as invalid Node-API status. |

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
    { description: "report_time", value: [1000] }
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
| 202 | Permission check failed. A non-system application uses the system API. |
| 33900001 | Service exception. Possible causes: <br>1. Node-API invocation exception, such as invalid Node-API status. <br>2. IPC request exception. |

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