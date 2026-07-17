# @ohos.multimodalAwareness.userStatus (用户状态感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供用户状态感知能力，包括用户手势识别、人脸位姿识别、手眼协同检测、用户吹气状态检测、用户情绪检测、用户环境音检测等功能。适用于需要感知用户状态来优化交互体验的场景，能够帮助应用提供更自然、更个性化的用户体验。模块采用订阅/回调机制，通过底层传感器数据采集、特征提取和状态判断三个阶段实现用户状态检测，开发者可根据业务需求订阅相应的检测功能。

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

| 名称 | 类型 | 只读 | 可选 | 说明                                               |
| --- | --- | --- | --- |--------------------------------------------------|
| deviceId | string | 否 | 否 | 表示设备ID。设备唯一标识符，用于标识和区分不同设备，字符串长度范围[0,64]。        |
| networkId | string | 否 | 否 | 表示设备网络ID。用于设备组网和跨设备通信的唯一网络标识，字符串长度范围[0,64]。      |
| deviceName | string | 否 | 否 | 表示设备名称。用户可自定义的设备显示名称，用于在界面中展示设备信息，字符串长度范围[0,64]。 |
| deviceType | [DeviceType](#devicetype) | 否 | 否 | 表示设备类型。                                          |

## UserStatusFeature

表示用户状态检测功能类型。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| GESTURES_RECOGNITION | 5 | 表示用户手势识别功能（100ms上报间隔）。 |
| ANTI_MISTOUCH | 6 | 表示防误触检测功能。 |
| QUICK_GESTURES_RECOGNITION | 7 | 表示用户快速手势识别功能（20ms上报间隔）。 |
| FACE_RELATIVE_POSITION_RECOGNITION | 8 | 表示人脸位姿识别功能（100ms上报间隔）。 |
| QUICK_FACE_RELATIVE_POSITION_RECOGNITION | 9 | 表示快速人脸位姿识别功能（20ms上报间隔）。 |
| HAND_GAZE_COORDINATION | 11 | 表示手眼协同检测功能。 |
| USER_BLOWING_STATUS | 12 | 表示用户吹气状态检测功能。 |
| USER_MOOD | 13 | 表示用户情绪检测功能。 |
| COMFORT_REMINDER | 15 | 表示铃声舒适检测功能。 |
| ENV_SOUND | 17 | 表示环境音检测功能。 |
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
| ENV_SOUND | 13 | 表示检测用户环境音强度。 |
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
| status | string | 是 | 否 | 表示特定功能下的多阶段检测状态。该字符串取值已表明响应的检测状态，字符串最大长度是64。 |
| result | number | 是 | 否 | 表示用户状态检测结果。0表示成功，非0表示失败。 |
| errCode | number | 是 | 否 | 表示业务错误码。0表示成功，非0表示失败。 |

## UserBlowData

表示用户吹气数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明                                                                 |
| --- | --- | --- | --- |--------------------------------------------------------------------|
| facePosition | number[] | 是 | 是 | 表示人脸相对于屏幕的坐标位置。数组长度为8，分别表示上下左右四个顶点的x、y坐标，归一化坐标系的取值范围是[0,640]。 |
| strengthLevel | number | 是 | 是 | 表示吹气力度。取值范围[1,12]。                                                 |
| blowDirection | number | 是 | 是 | 表示吹气方向。取值范围[0,2]。0：未吹气，1：底部麦克风，2：顶部麦克风。                            |
| emotion | number | 是 | 是 | 表示用户情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。           |
| isGazeStatus | boolean | 是 | 是 | 表示用户是否注视屏幕。取值范围[true,false]。                                       |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。数组长度为3，分别表示x、y、z三个方向的加速度分量，单位：m/s²。                |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。二维数组，外层表示多个点位的采样，内层为长度3的数组，分别表示x、y、z三个方向的加速度分量，单位：m/s²。      |

## UserEmotionData

表示用户情绪数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明                                                          |
| --- | --- | --- | --- |-------------------------------------------------------------|
| emotionRealTime | number | 是 | 是 | 表示用户实时情绪级别。取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。  |
| confidence | number | 是 | 是 | 表示用户情绪置信度。取值范围[0,100]                                  |
| isRealTime | boolean | 是 | 是 | 表示情绪数据是否为实时数据。取值范围[true,false]。                             |
| emotionNonRealTime | number[] | 是 | 是 | 表示用户非实时情绪级别。数组包含一段时间内采集的多个情绪值，每个元素取值范围[0,5]。0：非常愉悦，1：有点愉悦，2：平静，3：有点不愉悦，4：大怒，5：大哭。 |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。数组长度为3，分别表示x、y、z三个方向的加速度分量，单位：m/s²。                                    |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。二维数组，外层表示多个点位的采样，内层为长度3的数组，分别表示x、y、z三个方向的加速度分量，单位：m/s²。      |

## ComfortReminderData

表示舒适提醒数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示综合检测后的提醒级别。 |
| swingReminderData | [ReminderLevel](#reminderlevel) | 是 | 否 | 表示注视屏幕时提醒级别。 |
| eventType | number | 是 | 否 | 表示事件类型。取值为0或1，0表示注视事件，1表示环境音事件。 |

## UserFacesData

表示用户朝向屏幕相关的数据，继承自[UserStatusData](#userstatusdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明                                                                       |
| --- | --- | --- | --- |--------------------------------------------------------------------------|
| visualAngle | number[] | 是 | 是 | 表示用户看屏幕的视角。取值范围[0,90]。单位：deg。                                            |
| angularVelocity | number[] | 是 | 是 | 表示当前状态下设备的角速度。数组长度为3，分别表示绕x、y、z三个轴旋转的角速度分量，单位：rad/s。                     |
| gravityAcceleration | number[] | 是 | 是 | 表示当前状态下设备的重力加速度。数组长度为3，分别表示x、y、z三个方向的加速度分量，单位：m/s²。                      |
| linearAcceleration | number[][] | 是 | 是 | 表示当前状态下设备的线性加速度。二维数组，外层表示多个时间点的采样，内层为长度3的数组，分别表示x、y、z三个方向的加速度分量，单单位：m/s²。 |
| azimuth | number[] | 是 | 是 | 表示当前状态下设备的方位角。数组长度为3，分别表示偏航角（绕y轴）、俯仰角（绕x轴）和翻滚角（绕z轴），取值范围[0,360]。单位：deg。  |
| faceNum | number | 是 | 是 | 表示检测到的人脸数量。取值范围[0,3]。                                                    |

## UserGesturesData

表示用户手势数据，继承自[UserFacesData](#userfacesdata)。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明                                                                |
| --- | --- | --- | --- |-------------------------------------------------------------------|
| isHandExist | boolean | 是 | 是 | 表示用户手是否存在。取值范围[true,false]。                                       |
| handPosition | number[] | 是 | 是 | 表示手相对于屏幕的坐标位置。数组长度为8，分别表示上下左右四个顶点的x、y坐标，归一化坐标系的取值范围是[0,640]。 |
| motionGesture | number | 是 | 是 | 表示用户动态手势类型。取值范围[0,3]。0：上翻，1：下翻，2：抓屏，3：释放。                         |
| handType | number | 是 | 是 | 表示用户静态手势类型。取值范围[0,3]。0：掌型，1：拳型，2：剪刀，3：比心。                         |
| directionAngle | number[] | 是 | 是 | 表示用户手势与屏幕方向的夹角。数组包含手势在多个维度的角度值，每个元素取值范围[0,90]，单位：deg。             |
| gestureSpeed | number[] | 是 | 是 | 表示手势速度。数组长度为2，分别表示速度分量和默认值0，单位：帧/秒。                           |

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

订阅用户状态监控，以获取用户状态数据。调用subscribe()后，必须在使用完毕后调用unsubscribe()取消订阅以释放回调资源，未调用unsubscribe()会导致回调资源泄漏，影响应用性能。建议先调用configure()配置功能参数，再调用subscribe()开始订阅。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 是 | 回调函数，用于接收用户状态数据。当订阅的用户状态数据更新时会被调用。 |
| deviceInfo | [DeviceInfo](#deviceinfo)[] | 否 | 表示要开启用户状态监控的设备列表。当featureId为HAND_GAZE_COORDINATION时需要输入有效且非空的deviceInfo信息；其他featureId可省略此参数。如果输入空、undefined或null，则认为没有传入实际值。 |

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
  console.error(`subscribe failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.unsubscribe

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): number

取消订阅用户状态监控。与subscribe()方法成对使用，用于取消订阅回调并释放资源。必须在subscribe()之后调用，取消未订阅的featureId返回失败。建议在应用退出或不再需要监控时调用unsubscribe()。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明                                                            |
| --- | --- | --- |---------------------------------------------------------------|
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示要取消订阅的用户状态检测功能类型。对应subscribe时传入的featureId值。                 |
| callback | Callback<[UserStatusData](#userstatusdata)> | 否 | 表示取消指定的callback回调函数。如果输入空、undefined或null，则取消featureId订阅的所有通知事件。 |

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
  userStatus.unsubscribe(mistouchFeatureId);
} catch (err) {
  let error = err as BusinessError;
  console.error(`unsubscribe failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.configure

configure(featureId: UserStatusFeature, detail: string): number

配置功能参数。调用成功后，将更新指定功能的配置参数，影响后续该功能的检测行为。配置参数会修改检测算法的内部参数，如检测灵敏度、采样频率、启用的检测项等，从而改变检测性能和结果。建议在subscribe()之前调用configure()配置功能参数，确保配置在订阅时生效。configure()的配置参数会影响subscribe()订阅后接收到的用户状态数据的检测行为和精度。对于需要特定配置的功能（如USER_MOOD的实时/非实时模式），必须先configure()再subscribe()。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature) | 是 | 表示要配置的用户状态检测功能类型。 |
| detail | string | 是 | 配置参数，JSON格式字符串。包含params数组，每个参数包含description（参数名）和value（参数值数组）字段。具体格式和取值参见下方detail定义说明表格。 |

**detail定义说明**：

| featureId | description | value | 说明 |
| --- | --- | --- | --- |
| USER_MOOD | isRealTime | [ ] | isRealTime取值为0或1，0表示非实时，1表示实时。实时模式下获取数据会增加性能开销，建议根据业务需要选择合适模式以优化性能。 |
| - | atomicCapabilities | [ ] | atomicCapabilities取值可以包含至少一个或多个值，重复值会被自动去重。启用多个能力会增加计算负担，建议根据业务需求按需选择以优化性能。<br>5=原子重力传感器<br>8=原子线性加速度传感器<br>12=原子情绪能力 |
| GESTURES_RECOGNITION<br>QUICK_GESTURES_RECOGNITION | dynamicGestureTypes | [ ] | dynamicGestureTypes取值可以包含至少一个或多个值，重复值无效。启用多种手势类型会增加识别计算负担，建议按需选择以优化性能。<br>0=抓取<br>1=向下滑动<br>2=上翻初始手势<br>3=下翻初始手势<br>4=向上滑动<br>5=拳头变掌<br>6=消失 |
| - | staticGestureTypes | [ ] | staticGestureTypes取值可以包含至少一个或多个值，重复值无效。启用多种手势类型会增加识别计算负担，建议按需选择以优化性能。<br>7=手掌<br>8=剪刀手<br>9=拳头<br>10=爱心手势 |
| USER_BLOWING_STATUS | atomicCapabilities | [ ] | atomicCapabilities取值可以包含至少一个或多个值，重复值会被自动去重。启用多个能力会增加计算负担，建议根据业务需求按需选择以优化性能。<br>5=原子重力传感器<br>8=原子线性加速度传感器<br>11=原子吹气能力<br>12=原子情绪能力<br>15=原子屏幕注视能力 |

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
  console.info('configure result: ', result);
} catch (err) {
  let error = err as BusinessError;
  console.error(`configure failed. Code: ${error.code}, message: ${error.message}`);
}
```

## userStatus.queryCapabilities

queryCapabilities(capabilities: UserStatusAtomicCap[]): UserStatusAtomicCap[]

查询设备支持的原子化服务能力。该方法通过底层接口判断是否支持指定的原子化服务能力，返回设备实际支持的能力列表。

**起始版本**：26.0.0

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](#userstatusatomiccap)[] | 是 | 返回设备实际支持的原子化服务能力列表，为输入参数中设备支持的能力子集。可用于判断设备是否支持特定能力，用于后续调用前的能力校验。 |

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
  console.info('Query capabilities result: ', result);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Query capabilities failed. Code: ${error.code}, message: ${error.message}`);
}
```
