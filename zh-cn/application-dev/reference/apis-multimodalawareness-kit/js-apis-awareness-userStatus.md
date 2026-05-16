# @ohos.multimodalAwareness.userStatus (用户状态感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供用户状态感知能力，包括年龄群组检测等功能。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。从API version 24开始废弃，无替代接口。


## 导入模块

```ts
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## UserAgeGroup<sup>(deprecated)</sup>

表示用户具体的年龄分类群组，例如，儿童或成年人。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

| 名称                | 值  | 说明                   |
| ------------------- | ---- | ---------------------- |
| OTHERS  | 0    | 表示是成年人操作。 |
| CHILD  | 1    | 表示是儿童操作。 |

## UserClassification<sup>(deprecated)</sup>

表示用户年龄群组分类检测结果。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

| 名称                | 类型   |只读|可选| 说明                   |
| ------------------- | ---- |----|----| ---------------------- |
| ageGroup  | [UserAgeGroup](#useragegroupdeprecated)   |否|是| 表示具体的年龄群组（例如，儿童、成人）。 |
| confidence  | float    |否|是| 表示年龄群组检测结果的置信度，取值范围[0,1]的浮点数，数值越大代表置信度越高。 |

## DeviceType<sup>26+</sup>

表示设备类型。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。


| 名称 | 值 | 说明 |
| --- | --- | --- |
| UNKNOWN_TYPE | 0 | 表示设备类型未知。 |
| PC | 0x0C | 表示PC设备。 |
| PHONE | 0x0E | 表示手机设备。 |
| TABLET | 0x11 | 表示平板设备。 |

## DeviceInfo<sup>26+</sup>

表示设备信息。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| deviceId | string | 否 | 否 | 表示设备ID。 |
| networkId | string | 否 | 否 | 表示设备网络ID。 |
| deviceName | string | 否 | 否 | 表示设备名称。 |
| deviceType | [DeviceType](#devicetype) | 否 | 否 | 表示设备类型。 |

## UserStatusFeature<sup>26+</sup>

表示用户状态检测功能类型。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| GESTURES_RECOGNITION | 5 | 表示手势识别功能（100ms上报间隔）。 |
| ANTI_MISTOUCH | 6 | 表示防误触检测功能。 |
| QUICK_GESTURES_RECOGNITION | 7 | 表示快速手势识别功能（20ms上报间隔）。 |
| FACE_RELATIVE_POSITION_RECOGNITION | 8 | 表示面部相对位置识别功能（100ms上报间隔）。 |
| QUICK_FACE_RELATIVE_POSITION_RECOGNITION | 9 | 表示快速面部相对位置识别功能（20ms上报间隔）。 |
| HAND_GAZE_COORDINATION | 11 | 表示手眼协调（注意力）识别功能。 |
| USER_BLOWING_STATUS | 12 | 表示用户吹气状态检测功能。 |
| USER_MOOD | 13 | 表示用户情绪检测功能。 |
| COMFORT_REMINDER | 15 | 表示舒适提醒检测功能。 |
| ENV_SOUND | 17 | 表示环境声音检测功能。 |
| EXT_SCREEN_ANTI_MISTOUCH | 19 | 表示外屏防误触检测功能。 |

## UserStatusAtomicCap<sup>26+</sup>

表示用户状态原子能力类型。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| ATOMIC_UNKNOWN | 0 | 表示未知原子能力。 |
| FACE_RELATIVE_POSITION | 1 | 表示检测人脸相对于屏幕的位置。 |
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

## ReminderLevel<sup>26+</sup>

表示舒适提醒级别，用于触发特定提醒铃声。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| WEAK_REMINDER | 0 | 表示弱提醒级别。 |
| NORMAL_REMINDER | 1 | 表示普通提醒级别。 |

## UserStatusData<sup>26+</sup>

表示用户状态数据。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。


| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| feature | [UserStatusFeature](#userstatusfeature) | 否 | 否 | 表示用户状态检测功能类型。 |
| status | string | 否 | 否 | 表示单一感知功能下的多阶段检测状态。 |
| result | int | 否 | 否 | 表示用户状态检测结果。 |
| errCode | int | 否 | 否 | 表示业务错误码。 |

## UserBlowData<sup>26+</sup>

表示用户吹气数据，继承自[UserStatusData](#userstatusdata26)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| facePosition | double[] | 否 | 是 | 表示人脸相对于屏幕的位置。 |
| strengthLevel | int | 否 | 是 | 表示吹气力度级别。 |
| blowDirection | int | 否 | 是 | 表示吹气方向。 |
| emotion | int | 否 | 是 | 表示用户情绪级别。 |
| isGazeStatus | boolean | 否 | 是 | 表示用户是否注视屏幕。 |
| gravityAcceleration | double[] | 否 | 是 | 表示用户运动状态的重力加速度。 |
| linearAcceleration | double[][] | 否 | 是 | 表示用户运动状态的线性加速度。 |

## UserEmotionData<sup>26+</sup>

表示用户情绪数据，继承自[UserStatusData](#userstatusdata26)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| emotionRealTime | int | 否 | 是 | 表示用户实时情绪级别。 |
| confidence | int | 否 | 是 | 表示用户情绪置信度。 |
| isRealTime | boolean | 否 | 是 | 表示情绪数据是否为实时数据。 |
| emotionNonRealTime | int[] | 否 | 是 | 表示用户非实时情绪级别。 |
| gravityAcceleration | double[] | 否 | 是 | 表示用户运动状态的重力加速度。 |
| linearAcceleration | double[][] | 否 | 是 | 表示用户运动状态的线性加速度。 |

## ComfortReminderData<sup>26+</sup>

表示舒适提醒数据，继承自[UserStatusData](#userstatusdata26)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| fusionReminderData | [ReminderLevel](#reminderlevel) | 否 | 否 | 表示融合提醒数据。 |
| swingReminderData | [ReminderLevel](#reminderlevel) | 否 | 否 | 表示摆动提醒数据。 |
| eventType | int | 否 | 否 | 表示事件类型。 |

## UserFacesData<sup>26+</sup>

表示用户面部数据，继承自[UserStatusData](#userstatusdata26)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| visualAngle | double[] | 否 | 是 | 表示用户视角。 |
| angularVelocity | double[] | 否 | 是 | 表示用户运动状态的角速度。 |
| gravityAcceleration | double[] | 否 | 是 | 表示用户运动状态的重力加速度。 |
| linearAcceleration | double[][] | 否 | 是 | 表示用户运动状态的线性加速度。 |
| azimuth | double[] | 否 | 是 | 表示用户运动状态的方位角。 |
| faceNum | int | 否 | 是 | 表示检测到的人脸数量。 |

## UserGesturesData<sup>26+</sup>

表示用户手势数据，继承自[UserFacesData](#userfacesdata)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| isHandExist | boolean | 否 | 是 | 表示用户手是否存在。 |
| handPosition | double[] | 否 | 是 | 表示手相对于屏幕的位置。 |
| motionGesture | int | 否 | 是 | 表示用户动态手势类型。 |
| handType | int | 否 | 是 | 表示用户静态手势类型。 |
| directionAngle | double[] | 否 | 是 | 表示用户手势与屏幕方向的夹角。 |
| gestureSpeed | double[] | 否 | 是 | 表示手势速度。 |

## UserFaceAngleData<sup>26+</sup>

表示用户面部角度数据，继承自[UserStatusData](#userstatusdata26)。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| hpeNetworkId | string | 否 | 否 | 表示用户头部所面向的设备的网络ID。 |

## userStatus.on('userAgeGroupDetected')<sup>(deprecated)</sup>

 on(type: 'userAgeGroupDetected', callback: Callback&lt;UserClassification&gt;): void

订阅年龄群组检测功能。

订阅成功后，可以获取用户年龄群组的分类结果，应用可根据此结果做相应的内容推荐。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**设备行为差异**：该接口在Phone中可正常调用，在其他设备类型中返回801错误码。

> **说明：**
>
> 该接口仅在部分Phone中支持使用，当Phone设备不支持时返回801错误码。

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- |------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“userAgeGroupDetected”，表示年龄群组检测功能。 |
| callback | Callback&lt;[UserClassification](#userclassificationdeprecated)&gt; | 是   | 回调函数，返回检测结果。|

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status.|
| 33900002 | Subscription failed. Possible causes: <br>1. Callback registration failed. <br>2. Failed to bind the native object to the JS wrapper. <br>3. Node-API invocation exception, such as invalid Node-API status. <br>4. IPC request exception. |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.on('userAgeGroupDetected', (data: userStatus.UserClassification) => {
        console.info('callback succeeded, ageGroup:' + data.ageGroup + ", confidence:" + data.confidence);
    });
    console.info("on succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed on and err code is " + error.code);
}
```

## userStatus.off('userAgeGroupDetected')<sup>(deprecated)</sup>

off(type: 'userAgeGroupDetected', callback?: Callback&lt;UserClassification&gt;): void

取消订阅年龄群组检测功能。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**设备行为差异**：该接口在Phone中可正常调用，在其他设备类型中返回33900003错误码。

> **说明：**
>
> 该接口仅在部分Phone中支持使用，当Phone设备不支持时返回33900003错误码。

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“userAgeGroupDetected”，表示年龄群组检测功能。|
| callback | Callback&lt;[UserClassification](#userclassificationdeprecated)&gt; | 否   | 回调函数，返回检测结果。 |

**错误码**：

以下错误码的详细介绍请参见[用户状态感知错误码](errorcode-userStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 33900001 | Service exception. Possible causes: <br>1. System error, such as a null pointer and container-related exception. <br>2. Node-API invocation exception, such as invalid Node-API status. |
| 33900003 | Unsubscription failed. Possible causes: <br>1. Callback failure. <br>2. Node-API invocation exception, such as invalid Node-API status. <br>3. IPC request exception.|

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    userStatus.off('userAgeGroupDetected');
    console.info("off succeeded");
} catch (err) {
    let error = err as BusinessError;
    console.error("Failed off and err code is " + error.code);
}
```

## userStatus.subscribe<sup>26+</sup>

subscribe(featureId: UserStatusFeature, callback: Callback&lt;UserStatusData&gt;, deviceInfo?: DeviceInfo[]): int

订阅用户状态监控，以获取用户状态数据。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature26) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata26)> | 是 | 回调函数，返回用户状态数据。 |
| deviceInfo | [DeviceInfo](#deviceinfo26)[] | 否 | 表示要开启用户状态监控的设备列表。 |

**返回值**：

返回注册的回调ID。

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

## userStatus.unsubscribe<sup>26+</sup>

unsubscribe(featureId: UserStatusFeature, callback?: Callback&lt;UserStatusData&gt;): int

取消订阅用户状态监控。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature26) | 是 | 表示用户状态检测功能类型。 |
| callback | Callback<[UserStatusData](#userstatusdata26)> | 否 | 回调函数，返回用户状态数据。 |

**返回值**：

返回0表示操作成功；返回非零值表示操作失败。

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
    console.info(TAG, `unsubscribe failed, error: ${data.result}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error("unsubscribe failed, err code is " + error.code);
}
```

## userStatus.configure<sup>26+</sup>

configure(featureId: UserStatusFeature, detail: string): int

配置功能参数。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | [UserStatusFeature](#userstatusfeature26) | 是 | 表示要配置的用户状态检测功能类型。 |
| detail | string | 是 | 表示详细的配置参数，JSON格式。 |

**返回值**：

返回0表示操作成功；返回非零值表示操作失败。

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

try {
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
  const result = userStatus.configure(moodFeatureId, JSON.stringify(configData));
  console.log("configure result: ", result);
} catch (err) {
  let error = err as BusinessError;
  console.error("configure failed, err code is " + error.code);
}
```

## userStatus.queryCapabilities<sup>26+</sup>

queryCapabilities(capabilities: UserStatusAtomicCap[]): UserStatusAtomicCap[]

查询设备支持的原子能力。

**系统能力**：SystemCapability.MultimodalAwareness.UserStatus

**系统API**：此接口为系统接口。

**参数**：

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](#userstatusatomiccap26)[] | 是 | 表示要查询的原子能力列表。 |

**返回值**：

返回设备支持的原子能力列表。

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
  console.log("Query capabilities result: ", result);
} catch (err) {
  let error = err as BusinessError;
  console.error("Query capabilities failed, err code is " + error.code);
}
```

