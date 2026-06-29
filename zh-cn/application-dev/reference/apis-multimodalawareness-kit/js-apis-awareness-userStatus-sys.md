# @ohos.multimodalAwareness.userStatus (用户状态感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
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
| deviceId | string | 否 | 否 | 表示设备ID。字符串长度范围[0,64]。 |
| networkId | string | 否 | 否 | 表示设备网络ID。字符串长度范围[0,64]。 |
| deviceName | string | 否 | 否 | 表示设备名称。字符串长度范围[0,64]。 |
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

表示用户状态支持的原子化服务能力。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| ATOMIC_UNKNOWN | 0 | 表示未知的原子化服务能力。 |
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
| status | string | 是 | 否 | 表示特定功能下的多阶段检测状态。字符串长度范围[0,64]。 |
| result | number | 是 | 否 | 表示用户状态检测结果。0表示成功，非0表示失败。 |
| errCode | number | 是 | 否 | 表示业务错误码。0表示成功，非0表示失败。 |

## UserBlowData

表示用户吹气数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| facePosition | number[] | 是 | 是 | 表示人脸相对于屏幕的位置。取值范围[0,640]。 |
| strengthLevel | number | 是 | 是 | 表示吹气力度。取值范围[1,12]。 |
| blowDirection | number | 是 | 是 | 表示吹气方向。取值范围[0,2]。0：未吹气，1：底部麦克风，2：顶部麦克风。 |
| emotion | number | 是 | 是 | 表示用户情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 |
| isGazeStatus | boolean | 是 | 是 | 表示用户是否注视屏幕。取值范围[true,false]。 |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。单位为m/s²。 |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。单位为m/s²。 |

## UserEmotionData

表示用户情绪数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| emotionRealTime | number | 是 | 是 | 表示用户实时情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 |
| confidence | number | 是 | 是 | 表示用户情绪置信度。取值范围[0,100]。 |
| isRealTime | boolean | 是 | 是 | 表示情绪数据是否为实时数据。取值范围[true,false]。 |
| emotionNonRealTime | number[] | 是 | 是 | 表示用户非实时情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。单位为m/s²。 |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。单位为m/s²。 |

## ComfortReminderData

表示舒适提醒数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示综合检测后的提醒级别。 |
| swingReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示注视设备时提醒级别。 |
| eventType | number | 是 | 否 | 表示事件类型。取值范围[0,1]。0：注视事件，1：环境音事件。 |

## UserFacesData

表示用户朝向数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| visualAngle | number[] | 是 | 是 | 表示用户看屏幕的视角。取值范围[0,90]。 |
| angularVelocity | number[] | 是 | 是 | 表示当前状态下设备的角速度。单位为rad/s。 |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。单位为m/s²。 |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。单位为m/s²。 |
| azimuth | number[] | 是 | 是 | 表示当前状态下设备的方位角。取值范围[0,360]。 |
| faceNum | number | 是 | 是 | 表示检测到的人脸数量。取值范围[0,3]。 |

## UserGesturesData

表示用户手势数据，继承自[UserFacesData](#userfacesdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | 是 | 是 | 表示用户手是否存在。取值范围[true,false]。 |
| handPosition | number[] | 是 | 是 | 表示手相对于屏幕的位置。取值范围[0,640]。 |
| motionGesture | number | 是 | 是 | 表示用户动态手势类型。取值范围[0,3]。0：上翻，1：下翻，2：抓屏，3：释放。 |
| handType | number | 是 | 是 | 表示用户静态手势类型。取值范围[0,3]。0：掌型，1：拳型，2：剪刀，3：比心。 |
| directionAngle | number[] | 是 | 是 | 表示用户手势与屏幕方向的夹角。取值范围[0,90]。 |
| gestureSpeed | number[] | 是 | 是 | 表示手势速度。单位为帧/秒。 |

## UserFaceAngleData

表示用户朝向角度数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | 是 | 否 | 表示用户所面向的设备的网络ID。字符串长度范围[0,128]。 |

## userStatus.subscribe

subscribe(featureId: UserStatusFeature, callback: Callback&lt;UserStatusData&gt;, deviceInfo?: DeviceInfo[]): number

订阅用户状态监控，以获取用户状态数据。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 是 | 回调函数，返回用户状态数据。 |
| deviceInfo | [DeviceInfo](#deviceinfo)[] | 否 | 表示要开启用户状态监控的设备列表。当featureId为HAND_GAZE_COORDINATION时需要输入真实的deviceInfo信息。如果输入空、undefined或null，则认为没有传入实际值。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| number | 返回注册的回调ID。唯一标识对应回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

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

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): number

取消订阅用户状态监控。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 否 | 表示取消指定的callback通知。如果输入空、undefined或null，则取消featureId订阅的所有通知事件。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| number | 返回执行结果。返回0表示操作成功，非零值表示操作失败。 |


**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
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

configure(featureId: UserStatusFeature, detail: string): number

配置功能参数。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示要配置的用户状态检测功能类型。 |
| detail | string | 是 | 表示详细的配置参数，JSON格式。 |

**detail定义说明**：

| featureId | description | value | 说明 |
| --- | --- | --- | --- |
| USER_MOOD | isRealTime | [ ] | isRealTime取值为0或1，0表示非实时，1表示实时。 |
| - | atomicCapabilities | [ ] | atomicCapabilities取值可以包含至少一个或多个值，重复值无效。<br>5=原子重力传感器<br>8=原子线性加速度传感器<br>12=原子情绪能力 |
| GESTURES_RECOGNITION<br>QUICK_GESTURES_RECOGNITION | dynamicGestureTypes | [ ] | dynamicGestureTypes取值可以包含至少一个或多个值，重复值无效。<br>"fetch"=抓取<br>"slide_up"=向上滑动<br>"slide_down"=向下滑动<br>"start_up"=上翻初始手势<br>"start_down"=下翻初始手势<br>"fist_to_palm"=拳头变掌<br>"disappear"=消失 |
| - | staticGestureTypes | [ ] | staticGestureTypes取值可以包含至少一个或多个值，重复值无效。<br>"palm"=手掌<br>"fingerV"=剪刀手<br>"fist"=拳头<br>"heartGesture"=爱心手势 |
| USER_BLOWING_STATUS | atomicCapabilities | [ ] | atomicCapabilities取值可以包含至少一个或多个值，重复值无效。<br>5=原子重力传感器<br>8=原子线性加速度传感器<br>11=原子吹气能力<br>12=原子情绪能力<br>15=原子屏幕注视能力 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| number | 返回配置执行结果。返回0表示操作成功，非零值表示操作失败。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |

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

查询设备支持的原子化服务能力。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](#userstatusatomiccap)[] | 是 | 表示要查询的原子化服务能力列表。 |

**返回值**：

| 类型                           | 说明         |
| ---------------------------- | ---------- |
| [UserStatusAtomicCap](#userstatusatomiccap)[]| 返回设备支持的原子化服务能力列表。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| --- | --- |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |

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
