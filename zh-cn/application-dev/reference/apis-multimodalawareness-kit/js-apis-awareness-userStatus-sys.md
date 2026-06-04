# @ohos.multimodalAwareness.userStatus (用户状态感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @wyxpku-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供用户状态感知能力，包括手势检测、环境音检测等功能。

**起始版本**：26.0.0

> **说明：**
>
> 本模块为系统接口。

## 导入模块

```ts
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## DeviceType

表示设备类型。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| UNKNOWN_TYPE | 0 | 表示设备类型未知。 |
| PC | 0x0C | 表示PC设备。 |
| PHONE | 0x0E | 表示手机设备。 |
| TABLET | 0x11 | 表示平板设备。 |

## DeviceInfo

表示设备信息。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| deviceId | string | 否 | 否 | 表示设备ID。 |
| networkId | string | 否 | 否 | 表示设备网络ID。 |
| deviceName | string | 否 | 否 | 表示设备名称。 |
| deviceType | [DeviceType](#devicetype) | 否 | 否 | 表示设备类型。 |

## UserStatusFeature

表示用户状态检测功能类型。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| GESTURES_RECOGNITION | 5 | 表示手势识别功能（100ms上报间隔）。 |
| ANTI_MISTOUCH | 6 | 表示防误触检测功能。 |
| QUICK_GESTURES_RECOGNITION | 7 | 表示快速手势识别功能（20ms上报间隔）。 |
| FACE_RELATIVE_POSITION_RECOGNITION | 8 | 表示人脸位姿识别功能（100ms上报间隔）。 |
| QUICK_FACE_RELATIVE_POSITION_RECOGNITION | 9 | 表示快速人脸位姿识别功能（20ms上报间隔）。 |
| HAND_GAZE_COORDINATION | 11 | 表示手眼协同检测功能。 |
| USER_BLOWING_STATUS | 12 | 表示用户吹气状态检测功能。 |
| USER_MOOD | 13 | 表示用户情绪检测功能。 |
| COMFORT_REMINDER | 15 | 表示铃声舒适检测功能。 |
| ENV_SOUND | 17 | 表示环境声音检测功能。 |
| EXT_SCREEN_ANTI_MISTOUCH | 19 | 表示外屏防误触检测功能。 |

## UserStatusAtomicCap

表示用户状态原子能力类型。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| ATOMIC_UNKNOWN | 0 | 表示未知原子能力。 |
| FACE_RELATIVE_POSITION | 1 | 表示检测人脸相对于屏幕。 |
| FACE_NUM_CHANGE | 2 | 表示检测人脸数量变化。 |
| GESTURE | 3 | 表示检测用户手势。 |
| FACE_ANGLE | 4 | 表示检测人脸相对于屏幕的角度。 |
| SENSOR_GRAVITY | 5 | 表示检测传感器重力数据。 |
| SENSOR_GYROSCOPE | 6 | 表示检测传感器陀螺仪数据。 |
| SENSOR_ACCELEROMETER | 7 | 表示检测传感器加速度计数据。 |
| SENSOR_LINEAR_ACCELERATION | 8 | 表示检测传感器线性加速度数据。 |
| SENSOR_ROTATION_VECTOR | 9 | 表示检测传感器旋转矢量数据。 |
| SENSOR_ORIENTATION | 10 | 表示检测传感器方向数据。 |
| BLOWING_STATUS | 11 | 表示检测用户吹气数据。 |
| MOOD_STATUS | 12 | 表示检测用户情绪数据。 |
| ENV_SOUND | 13 | 表示检测用户环境声音强度。 |
| NOISE_SOUND | 14 | 表示检测用户噪音强度。 |
| EYE_GAZE_SCREEN | 15 | 表示检测用户是否注视屏幕。 |

## ReminderLevel

表示提醒强度级别，触发提醒铃声时使用。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| WEAK_REMINDER | 0 | 表示弱提醒级别。 |
| NORMAL_REMINDER | 1 | 表示正常提醒级别。 |

## UserStatusData

表示用户状态数据。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| feature | [UserStatusFeature](#userstatusfeature) | 是 | 否 | 表示用户状态检测功能类型。 |
| status | string | 是 | 否 | 表示特定功能下的多阶段检测状态。 |
| result | int | 是 | 否 | 表示用户状态检测结果。 |
| errCode | int | 是 | 否 | 表示业务错误码，默认0表示成功。|

## UserBlowData

表示用户吹气数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| facePosition | double[] | 是 | 是 | 表示人脸相对于屏幕的位置。 |
| strengthLevel | int | 是 | 是 | 表示吹气力度。 |
| blowDirection | int | 是 | 是 | 表示吹气方向。 |
| emotion | int | 是 | 是 | 表示用户情绪级别。 |
| isGazeStatus | boolean | 是 | 是 | 表示用户是否注视屏幕。 |
| gravityAcceleration | double[] | 是 | 是 | 表示当前状态下设备的重力加速度。 |
| linearAcceleration | double[][] | 是 | 是 | 表示当前状态下设备的线性加速度。 |

## UserEmotionData

表示用户情绪数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| emotionRealTime | int | 是 | 是 | 表示用户实时情绪级别。 |
| confidence | int | 是 | 是 | 表示用户情绪置信度。 |
| isRealTime | boolean | 是 | 是 | 表示情绪数据是否为实时数据。 |
| emotionNonRealTime | int[] | 是 | 是 | 表示用户非实时情绪级别。 |
| gravityAcceleration | double[] | 是 | 是 | 表示当前状态下设备的重力加速度。 |
| linearAcceleration | double[][] | 是 | 是 | 表示当前状态下设备的线性加速度。 |

## ComfortReminderData

表示舒适提醒数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示综合检测后的提醒级别。 |
| swingReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示注视设备时提醒级别。 |
| eventType | int | 是 | 否 | 表示事件类型。 |

## UserFacesData

表示用户朝向数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| visualAngle | double[] | 是 | 是 | 表示用户看屏幕的视角。 |
| angularVelocity | double[] | 是 | 是 | 表示当前状态下设备的角速度。 |
| gravityAcceleration | double[] | 是 | 是 | 表示当前状态下设备的重力加速度。 |
| linearAcceleration | double[][] | 是 | 是 | 表示当前状态下设备的线性加速度。 |
| azimuth | double[] | 是 | 是 | 表示当前状态下设备的方位角。 |
| faceNum | int | 是 | 是 | 表示检测到的人脸数量。 |

## UserGesturesData

表示用户手势数据，继承自[UserFacesData](#userfacesdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | 是 | 是 | 表示用户手是否存在。 |
| handPosition | double[] | 是 | 是 | 表示手相对于屏幕的位置。 |
| motionGesture | int | 是 | 是 | 表示用户动态手势类型。 |
| handType | int | 是 | 是 | 表示用户静态手势类型。 |
| directionAngle | double[] | 是 | 是 | 表示用户手势与屏幕方向的夹角。 |
| gestureSpeed | double[] | 是 | 是 | 表示手势速度。 |

## UserFaceAngleData

表示用户朝向角度数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | 是 | 否 | 表示用户所面向的设备的网络ID。 |

## userStatus.subscribe

subscribe(featureId: UserStatusFeature, callback: Callback&lt;UserStatusData&gt;, deviceInfo?: DeviceInfo[]): int

订阅用户状态监控，以获取用户状态数据。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 是 | 回调函数，返回用户状态数据。 |
| deviceInfo | [DeviceInfo](#deviceinfo)[] | 否 | 表示要开启用户状态监控的设备列表。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| int | 返回注册的回调ID。唯一标识对应回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind native object to JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

**示例**：

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

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): int

取消订阅用户状态监控。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 否 | 回调函数，返回用户状态数据。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| int | 返回配置执行结果。返回0表示操作成功，非零值表示操作失败。 |


**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 801 | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900003 | Unsubscription failed. Possible causes: <br>1. Callback failure. <br>2. Node-API invocation exception, such as invalid Node-API status. <br>3. IPC request exception. |

**示例**：

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

configure(featureId: UserStatusFeature, detail: string): int

配置功能参数。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示要配置的用户状态检测功能类型。 |
| detail | string | 是 | 表示详细的配置参数，JSON格式。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| int | 返回配置执行结果。返回0表示操作成功，非零值表示操作失败。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 33900001 | Service exception. Possible causes: <br>1. Invalid parameter. <br>2. Node-API invocation exception, such as invalid Node-API status. |

**示例**：

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

查询设备支持的原子能力。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](#userstatusatomiccap)[] | 是 | 表示要查询的原子能力列表。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| [UserStatusAtomicCap](#userstatusatomiccap)[]| 返回设备支持的原子能力列表。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission check failed. A non-system application uses the system API. |
| 33900001 | Service exception. Possible causes: <br>1. Node-API invocation exception, such as invalid Node-API status. <br>2. IPC request exception. |

**示例**：

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
