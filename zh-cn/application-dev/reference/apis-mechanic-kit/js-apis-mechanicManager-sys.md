# @ohos.distributedHardware.mechanicManager (机械体控制模块)(系统接口)
<!--Kit: Mechanic Kit-->
<!--Subsystem: Mechanic-->
<!--Owner: @qxqxqxqxqx-->
<!--Designer: @peter__1024-->
<!--Tester: @Aullar-->
<!--Adviser: @hu-zhiqiong-->

本模块提供与机械体设备交互的能力，包括设备连接管理、控制和监控功能。

> **说明：**
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.distributedHardware.mechanicManager (机械体控制模块)](js-apis-mechanicManager.md)。

## 导入模块

```js
import { mechanicManager } from '@kit.MechanicKit';
```

## mechanicManager.setUserOperation

setUserOperation(operation: Operation, mac: string, params: string): void

设置用户的连接或断开操作。

**需要权限**：ohos.permission.CONNECT_MECHANIC_HARDWARE

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| operation | [Operation](#operation) | 是 | 操作类型。 |
| mac | string | 是 | 机械体设备MAC地址。 |
| params | string | 是 | 操作参数。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**示例：**

```ts
console.info('User operate');
mechanicManager.setUserOperation(mechanicManager.Operation.CONNECT, "58:51:9e:e7:79:6d", "operatingParams");
console.info('User operation was successful');
```

## mechanicManager.setCameraTrackingLayout

setCameraTrackingLayout(trackingLayout: CameraTrackingLayout): void

设置当前机械体设备摄像头跟踪布局。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| trackingLayout | [CameraTrackingLayout](js-apis-mechanicManager.md#cameratrackinglayout) | 是 | 摄像头跟踪布局。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
console.info('Set layout');
mechanicManager.setCameraTrackingLayout(mechanicManager.CameraTrackingLayout.LEFT);
console.info('Set layout successful');
```

## mechanicManager.rotate

rotate(mechId: number, angles: RotationAngles, duration: number): Promise\<Result>

将机械体设备旋转到相对角度。使用Promise异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| angles | [RotationAngles](#rotationangles) | 是 | 相对当前位置的旋转角度。 |
| duration | number | 是 | 旋转持续时间，单位：ms。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise对象，返回旋转执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Start rotate');
let degree: mechanicManager.RotationAngles = {
  yaw: 0.1 * Math.PI,
  roll: 0.0,
  pitch: 0.0
}
mechanicManager.rotate(0, degree, 500)
  .then((result: mechanicManager.Result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('End rotation');
```

## mechanicManager.rotateToEulerAngles

rotateToEulerAngles(mechId: number, angles: EulerAngles, duration: number): Promise\<Result>

将机械体设备旋转到绝对角度。使用Promise异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| angles | [EulerAngles](#eulerangles) | 是 | 绝对角度。 |
| duration | number | 是 | 旋转持续时间，单位：ms。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise对象，返回旋转执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
let degree: mechanicManager.EulerAngles = {
  yaw: 0.9 * Math.PI,
  roll: 0.9 * Math.PI,
  pitch: 0.9 * Math.PI
}
mechanicManager.rotateToEulerAngles(0, degree, 500)
  .then((result: mechanicManager.Result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('End rotation');
```

## mechanicManager.getMaxRotationTime

getMaxRotationTime(mechId: number): number

获取机械体设备的最大连续旋转持续时间。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| number | 最大旋转持续时间，单位：ms。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息  |
| -------- | -------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Query maximum rotation time');
let maxTime = mechanicManager.getMaxRotationTime(0);
console.info(`'Query maximum rotation time successful, maximum time:' ${maxTime}`);
```

## mechanicManager.getMaxRotationSpeed

getMaxRotationSpeed(mechId: number): RotationSpeed

获取机械体设备的最大旋转速度。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| [RotationSpeed](#rotationspeed) | 最大旋转速度，仅返回速度的绝对值。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Query rotation speed');
let speedLimit: mechanicManager.RotationSpeed = mechanicManager.getMaxRotationSpeed(0);
console.info(`'Query rotation speed successful, speed limit information:' ${speedLimit}`);
```

## mechanicManager.rotateBySpeed

rotateBySpeed(mechId: number, speed: RotationSpeed, duration: number): Promise\<Result>

以指定速度旋转当前机械体设备。使用Promise异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| speed | [RotationSpeed](#rotationspeed) | 是 | 指定旋转速度。最大旋转速度不超过getMaxRotationSpeed的返回值大小，如果超过最大速度，默认取最大值。 |
| duration | number | 是 | 旋转持续时间，单位：ms。最大时间不超过getMaxRotationTime的返回值大小，如果超过最大时间，默认取最大值。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise\<[Result](#result)> | Promise对象，返回旋转执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Start rotate');
let degree: mechanicManager.RotationSpeed = {
  yawSpeed: 3 * Math.PI,
  rollSpeed: 3 * Math.PI,
  pitchSpeed: 3 * Math.PI
}
mechanicManager.rotateBySpeed(0, degree, 500)
  .then((result) => {
    console.info(`'Rotate result:' ${result}`);
  });
console.info('Rotate finish');
```

## mechanicManager.stopMoving

stopMoving(mechId: number): Promise\<void>

停止机械体设备的移动。使用Promise异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Stop moving');
mechanicManager.stopMoving(0)
  .then(() => {
    console.info('Get stop complete');
  });
console.info('Stop succeeded');
```

## mechanicManager.getCurrentAngles

getCurrentAngles(mechId: number): EulerAngles

获取指定机械体设备相对于初始位置的当前旋转角度。

> **说明：**
>
> 初始位置：机械体设备初始化的位置，坐标为（0， 0， 0）。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| [EulerAngles](#eulerangles) | 机械体设备的当前旋转角度。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Query current location');
let currentAngles: mechanicManager.EulerAngles = mechanicManager.getCurrentAngles(0);
console.info(`'Query current location, location:' ${currentAngles}`);
```

## mechanicManager.getRotationLimits

getRotationLimits(mechId: number): RotationLimits

获取指定机械体设备相对于初始位置的最大旋转角度。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| [RotationLimits](#rotationlimits) | 最大旋转角度。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Query rotation limit information');
let degreeLimit: mechanicManager.RotationLimits = mechanicManager.getRotationLimits(0);
console.info(`'Query the rotation limit information successfully, limit information:' ${degreeLimit}`);
```

## mechanicManager.on('rotationAxesStatusChange')

on(type: 'rotationAxesStatusChange', callback: Callback\<RotationAxesStateChangeInfo>): void

注册旋转轴状态变化事件的回调监听。使用callback异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| type | 'rotationAxesStatusChange' | 是 | 注册监听事件的类型。取值为：'rotationAxesStatusChange'。 |
| callback | Callback\<[RotationAxesStateChangeInfo](#rotationaxesstatechangeinfo)> | 是 | 回调函数，返回机械体设备旋转轴状态变化信息。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |

**示例：**

```ts
console.info('Register Axis Status listener');
mechanicManager.on("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Successful registration');
```

## mechanicManager.off('rotationAxesStatusChange')

off(type: 'rotationAxesStatusChange', callback?: Callback\<RotationAxesStateChangeInfo>): void

取消注册旋转轴状态变化事件的回调监听。使用callback异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| type | 'rotationAxesStatusChange' | 是 | 取消注册监听事件的类型。取值为：'rotationAxesStatusChange'。 |
| callback | Callback\<[RotationAxesStateChangeInfo](#rotationaxesstatechangeinfo)> | 否 |  mechanicManager.off('rotationAxesStatusChange')注册的回调函数。不填时默认取消所有注册的回调函数。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |

**示例：**

```ts
console.info('Unregister Axis Status listener');
mechanicManager.off("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Unregister successfully');
```

## mechanicManager.getRotationAxesStatus

getRotationAxesStatus(mechId: number): RotationAxesStatus

获取当前机械体设备旋转轴的状态。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| [RotationAxesStatus](#rotationaxesstatus) | 旋转轴状态。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
console.info('Query the rotation axis status');
let axisStatus: mechanicManager.RotationAxesStatus = mechanicManager.getRotationAxesStatus(0);
console.info(`'Query the rotation axis status successfully, axis state:' ${axisStatus}`);
```

## mechanicManager.searchTarget<sup>21+<sup>
searchTarget(target: TargetInfo, params: SearchParams): Promise\<SearchResult>

旋转机械体一周搜索目标。使用Promise异步回调。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**
| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| target | [TargetType](#targettype21) | 是 | 目标人脸信息。 |
| params | [SearchParams](#searchparams21) | 是 | 搜索方向。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise\<[SearchResult](#searchresult21)> | Promise对象，返回搜索的结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |
| 33300004 | Camera not opened. |

**示例：**

```ts
let targetInfo: mechanicManager.TargetInfo = {
    targetType: mechanicManager.TargetType.HUMAN_FACE
};
let searchParams: mechanicManager.SearchParams = {
    direction: mechanicManager.SearchDirection.DEFAULT
}
mechanicManager.searchTarget(targetInfo,
    searchParams).then((searchResult) => {
    console.info(`'result:' ${searchResult}`);
});
```

## mechanicManager.move

move(mechId: number, params: MoveParams): Promise&lt;Result&gt;

以特定参数移动一个机械体设备。
  
**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| params | [MoveParams](#moveparams) | 是 | 移动参数。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt; | Promise对象，返回移动执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let mechId: number = 0;
let moveParams: mechanicManager.MoveParams = {
    distance: 0,
    angle: 0,
    speedGear: undefined,
    mode: undefined
};
try {
  mechanicManager.move(mechId, moveParams).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.moveBySpeed

moveBySpeed(mechId: number, params: SpeedParams, duration: number): Promise&lt;Result&gt;

以特定速度移动一个机械体设备。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| params | [SpeedParams](#speedparams) | 是 | 移动参数。|
| duration | number | 是 | 移动时长，单位ms。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise对象，返回移动执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let mechId: number = 0;
let speedParams: mechanicManager.SpeedParams = {
    speed: 0,
    angle: 0,
    mode: undefined
};
let duration: number = 1;
try {
  mechanicManager.moveBySpeed(mechId, speedParams, duration).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.turnBySpeed

turnBySpeed(mechId: number, angleSpeed: number, duration: number): Promise&lt;Result&gt;

以固定速度原地旋转。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| angleSpeed | number | 是 | 角速度。|
| duration | number | 是 | 转动时长，单位ms。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise对象，返回旋转执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let mechId: number = 0;
let angleSpeed: number = 1.2;
let duration: number = 1;
try {
  mechanicManager.turnBySpeed(mechId, angleSpeed, duration).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.isSupportAction

isSupportAction(mechId: number, actionType: ActionType): boolean

判断是否支持某个动作。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| actionType | [ActionType](#actiontype) | 是 | 动作序列类型。|

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| boolean | 是否支持该特定动作。true表示支持，false表示不支持。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |

**示例：**

```ts
let mechId: number = 0;
let actionType = mechanicManager.ActionType.HEAD_UP;
try {
  let isSupported = mechanicManager.isSupportAction(mechId, actionType);
  console.info(`isSupported: ${isSupported}`);
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.doAction

doAction(mechId: number, actionType: ActionType): Promise&lt;Result&gt;

执行一个动作序列。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |
| actionType | [ActionType](#actiontype) | 是 | 动作序列类型。|

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise对象，返回执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let mechId: number = 0;
let actionType = mechanicManager.ActionType.HEAD_UP;
try {
  mechanicManager.doAction(mechId, actionType).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.subscribe

subscribe(events: MechEventType[], callback: Callback&lt;MechEvent&gt;): void

订阅机械体设备事件回调。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| events | [MechEventType](#mecheventtype) | 是 | 订阅的事件列表。 |
| callback | Callback&lt;[MechEvent](#mechevent)&gt; | 是 | 回调函数，返回订阅的机械体设备事件。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let eventsSet: Set<mechanicManager.MechEventType> = new Set();
let events = Array.from(eventsSet);
try {
  mechanicManager.subscribe(events, (event: mechanicManager.MechEvent) => {
    console.info('subscribe callback');
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.unSubscribe

unSubscribe(events: MechEventType[]): void

取消事件注册。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| events | [MechEventType](#mecheventtype) | 是 | 订阅的事件列表。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 202 | Not system application. |
| 33300001 | Service exception. |
| 33300002 | Device not connected. |
| 33300003 | Feature not supported. |

**示例：**

```ts
let eventsSet: Set<mechanicManager.MechEventType> = new Set();
let events = Array.from(eventsSet);
try {
  mechanicManager.unSubscribe(events);
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.connectDevice

connectDevice(addrInfo: AddressInfo, params: ConnectParam): Promise&lt;AttachStateChangeInfo&gt;

基于地址连接设备。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| addrInfo | [AddressInfo](#addressinfo) | 是 | 地址信息。 |
| params | [ConnectParam](#connectparam) | 是 | 操作参数。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[AttachStateChangeInfo](#attachstatechangeinfo)&gt;| Promise对象，返回设备附加状态。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**示例：**

```ts
let addrInfo: mechanicManager.AddressInfo = {
  address: '123',
  addressType: mechanicManager.AddressType.BLE_ADDR
}
let params: mechanicManager.ConnectParam = {
  deviceName: "deviceName",
  custdata: '123',
  identifier: Number('0x551b9225')
}
try {
  mechanicManager.connectDevice(addrInfo, params)
    .then((info: mechanicManager.AttachStateChangeInfo) => {
      console.info(`connectDevice -- info: ${JSON.stringify(info)}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## mechanicManager.disconnectDevice

disconnectDevice(mechId: number): Promise&lt;Result&gt;

基于机械体设备ID断开设备。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

**参数：**

| 参数名     | 类型                    | 必填 | 说明   |
| ---------- | ---------------------- | ---- | ----- |
| mechId | number | 是 | 机械体设备ID。 |

**返回值：**

| 类型                                        | 说明        |
| ------------------------------------------- | --------- |
| Promise&lt;[Result](#result)&gt;| Promise对象，返回执行结果。 |

**错误码：**

以下的错误码的详细介绍请参见[机械体控制模块错误码](errorcode-mechanic.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息           |
| -------- | ----------------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 33300001 | Service exception. |

**示例：**

```ts
let mechId: number = 0;
try {
  mechanicManager.disconnectDevice(mechId).then((result: mechanicManager.Result) => {
    console.info(`'result:' ${result}`);
  });
} catch (e) {
  console.error(`Code is ${e.code}, message is ${e.message}`);
}
```

## RotationAngles

相对当前位置的旋转角度。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| yaw | number | 否 | 是 | 偏航角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |
| roll | number | 否 | 是 | 横滚角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |
| pitch | number | 否 | 是 | 俯仰角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |

## EulerAngles

相对于初始位置的绝对欧拉角。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| yaw | number | 否 | 是 | 偏航角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |
| roll | number | 否 | 是 | 横滚角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |
| pitch | number | 否 | 是 | 俯仰角，范围为[-2\*Math.PI， 2\*Math.PI]，以弧度为单位。 |

## RotationSpeed

旋转速度。负值表示顺时针旋转，正值表示逆时针旋转。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| yawSpeed | number | 否| 是 | 偏航速度，以弧度每秒为单位。 |
| rollSpeed | number | 否 | 是 | 横滚速度，以弧度每秒为单位。 |
| pitchSpeed | number | 否 | 是 | 俯仰速度，以弧度每秒为单位。 |

## RotationLimits

相对于初始位置的旋转角度限制。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| negativeYawMax | number | 否 | 否 | 最大偏航旋转角度（负方向），范围为[-2\*Math.PI， 0]，以弧度为单位。如果值小于或等于 -2\*Math.PI，则没有限制。 |
| positiveYawMax | number | 否 | 否 | 最大偏航旋转角度（正方向），范围为[0， 2\*Math.PI]，以弧度为单位。如果值大于或等于 2\*Math.PI，则没有限制。 |
| negativeRollMax | number | 否 | 否 | 最大横滚旋转角度（负方向），范围为[-2\*Math.PI, 0]，以弧度为单位。如果值小于或等于 -2\*Math.PI，则没有限制。 |
| positiveRollMax | number | 否 | 否 | 最大横滚旋转角度（正方向），范围为[0， 2\*Math.PI]，以弧度为单位。如果值大于或等于 2\*Math.PI，则没有限制。 |
| negativePitchMax | number | 否 | 否 | 最大俯仰旋转角度（负方向），范围为[-2\*Math.PI， 0]，以弧度为单位。如果值小于或等于 -2\*Math.PI，则没有限制。 |
| positivePitchMax | number | 否 | 否 | 最大俯仰旋转角度（正方向），范围为[0， 2\*Math.PI]，以弧度为单位。如果值大于或等于 2\*Math.PI，则没有限制。 |

## RotationAxesStatus

旋转轴状态。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| yawEnabled | boolean | 否 | 否 | 是否启用了偏航轴，true表示已启用，false表示已禁用。 |
| rollEnabled | boolean | 否 | 否 | 是否启用了横滚轴，true表示已启用，false表示已禁用。 |
| pitchEnabled | boolean | 否 | 否 | 是否启用了俯仰轴，true表示已启用，false表示已禁用。 |
| yawLimited | [RotationAxisLimited](#rotationaxislimited) | 否 | 是 | 偏航轴限位状态。 |
| rollLimited | [RotationAxisLimited](#rotationaxislimited) | 否 | 是 | 横滚轴限位状态。 |
| pitchLimited | [RotationAxisLimited](#rotationaxislimited) | 否 | 是 | 俯仰轴限位状态。 |

## RotationAxisLimited

旋转轴限位状态的枚举。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称         | 值  | 说明              |
| ----------- | ---- | --------------- |
| NOT_LIMITED | 0 | 无限制 |
| NEGATIVE_LIMITED | 1 | 负方向受限，可以向相反方向转动。 |
| POSITIVE_LIMITED | 2 | 正方向受限，可以向相反方向转动。 |

## RotationAxesStateChangeInfo

旋转轴状态变化信息。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| mechId | number | 否 | 否 | 机械体设备ID。 |
| status | [RotationAxesStatus](#rotationaxesstatus)| 否 | 否 | 旋转轴状态。 |

## Operation

用户操作的枚举。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称         | 值  | 说明              |
| ----------- | ---- | --------------- |
| CONNECT | 0 | 连接。 |
| DISCONNECT | 1 | 断开。 |

## Result

旋转执行结果的枚举。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称         | 值  | 说明              |
| ----------- | ---- | --------------- |
| COMPLETED | 0 | 执行完成。 |
| INTERRUPTED | 1 | 执行被打断。 |
| LIMITED | 2 | 执行受最大旋转角度限制。 |
| TIMEOUT | 3 | 执行超时。 |
| TERMINATE_OBSTACLE<sup>26.0.0+<sup> | 4 | 障碍物导致终止。 |
| TERMINATE_CLIFF<sup>26.0.0+<sup> | 5 | 悬崖导致终止。 |
| SYSTEM_ERROR | 100 | 系统错误。 |

## TargetType<sup>21+<sup>

目标人脸信息的枚举。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| HUMAN_FACE | int | 0 | 目标人脸信息。 |

## SearchDirection<sup>21+<sup>

系统默认的搜索方向。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| DEFAULT | int | 0 | 系统默认方向  |
| LEFTWARD | int | 1 | 左向，即顺时针方向。 |
| RIGHTWARD | int | 2 | 右向，即逆时针方向。 |
  
 ## TargetInfo<sup>21+<sup>

搜索目标的相关信息。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| targetType | [TargetType](#targettype21) | 否 | 否 | 搜索目标的相关信息。 |

## SearchParams<sup>21+<sup>

指定搜索的方向。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| direction | [SearchDirection](#searchdirection21) | 否 | 否 | 搜索的方向。 |

## SearchResult<sup>21+<sup>

显示搜索命令的执行结果。

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| targetCount | number | 否 | 否 | 搜索到的目标数量。 |

## MoveParams

设备移动参数。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| distance | number | 否 | 否 | 移动距离（取值限定为整数）。|
| angle | number | 否 | 否 | 转动角度。|
| speedGear | [SpeedGear](#speedgear) | 否 | 是 | 速度档位。|
| mode | [MarchingMode](#marchingmode) | 否 | 是 | 行进方式。|

## SpeedParams

速度控制参数。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| speed | number | 否 | 否 | 转动或移动速度（取值限定为整数）。|
| angle | number | 否 | 否 | 转动角度。|
| mode | [MarchingMode](#marchingmode) | 否 | 是 | 行进方式。|

## SpeedGear

速度档位枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| LOW_SPEED  | int | 0 | 低速档定义。 |
| MIDDLE_SPEED  | int | 1 | 中速档定义，默认值即为中速。 |
| HIGH_SPEED   | int | -1 | 高速档定义。 |

## MarchingMode

行进模式枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| TURN_THEN_MOVE  | int | 0 | 先转动再移动。 |
| TURNING_MOVING  | int | 1 | 边移动边转动。 |

## ActionType

动作序列类型枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| LANDSCAPE_PORTRAIT_SWITCH  | int | 0 | 横竖屏旋转。 |
| PATROL_MODE  | int | 1 | 巡桌模式。 |
| GREET_MODE  | int | 2 | 迎人模式。 |
| HEAD_UP  | int | 3 | 仰头。 |
| HEAD_UP_SLIGHTLY  | int | 4 | 微抬。 |
| EYE_LEVEL  | int | 5 | 平视。 |
| HEAD_DOWN_SLIGHTLY  | int | 6 | 微低。 |
| HEAD_DOWN  | int | 7 | 下俯到底。 |
| HEAD_WIGGLE  | int | 8 | 晃头。 |
| NOD  | int | 9 | 点头。 |
| HEAD_SHAKE  | int | 10 | 摇头。 |
| HEAD_TURN_TO_BASE  | int | 11 | 头向底座回正。 |
| BASE_TURN_TO_HEAD  | int | 12 | 底座向头回正。 |
| FRONT_TO_BACK_FLIP  | int | 13 | 云台前后方向翻转。 |
| HAPPY  | int | 1000 | 开心动作。 |
| ANGRY  | int | 1001 | 生气动作。 |
| SAD  | int | 1002 | 悲伤动作。 |
| SCARED  | int | 1003 | 惊吓动作。 |
| DANCE  | int | 2000 | 舞蹈动作。 |
| ACTING_CUTE  | int | 2001 | 卖萌动作。 |
| CELEBRATE  | int | 2002 | 庆祝动作。 |
| WAKEUP  | int | 2003 | 唤醒动作。 |
| SLEEP  | int | 2004 | 休眠动作。 |
| LOW_POWER  | int | 2005 | 低电量动作。 |
| THINKING  | int | 2006 | 思考中动作。 |

## MechEvent

机械体设备事件定义。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| mechId | number | 否 | 否 | 机械体设备ID。 |
| event | [MechEventType](#mecheventtype) | 否 | 否 | 事件类型。 |

## MechEventType

机械体设备事件定义。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| DEVICE_ADSORBED  | int | 0 | 吸附事件。 |
| DEVICE_UNADSORBED  | int | 1 | 未吸附事件。 |
| REACH_CLIFF  | int | 2 | 移动中遇到悬崖。 |
| REACH_OBSTACLE  | int | 3 | 移动中遇到障碍。 |
| LOW_POWER  | int | 4 | 设备低电量。 |

## AddressInfo

配件设备信息定义。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| address | string | 否 | 否 | 配件设备地址。 |
| addressType | [AddressType](#addresstype) | 否 | 否 | 地址类型。 |

## AddressType

机械体设备地址类型。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| BLE_ADDR  | int | 0 | 机械体设备蓝牙地址类型。 |

## ConnectParam

连接参数定义。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| deviceName | string | 否 | 是 | 机械体设备名称。 |
| identifier | number | 否 | 是 | 当前设备标识（取值限定为整数）。 |
| custdata | string | 否 | 否 | 发现设备时携带的数据。 |

## AttachStateChangeInfo

连接参数定义。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| state | [AttachState](#attachstate) | 否 | 否 | 附加状态。 |
| mechInfo | [MechInfo](#mechinfo) | 否 | 否 | 机械体设备信息。 |

## AttachState

机械体设备附加状态。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| ATTACHED  | int | 0 | 设备挂载。 |
| DETACHED  | int | 1 | 设备卸载。 |

## MechInfo

机械体设备信息。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称   | 类型 | 只读 | 可选 | 说明|
| ----- | ---- | ---- | --- | --- |
| mechId | number | 否 | 否 | 机械体设备ID。 |
| mechInfo | [MechDeviceType](#mechdevicetype) | 否 | 否 | 机械设备类型。 |
| mechName | string | 否 | 否 | 机械体设备名称。 |

## MechDeviceType

机械体设备类型枚举。

**起始版本**：26.0.0

**系统能力**：SystemCapability.Mechanic.Core

**系统接口**：该接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| ----------- | ------|---- | --------------- |
| GIMBAL_DEVICE  | int | 0 | 云台设备类型。 |
| DESKTOP_GIMBAL_DEVICE  | int | 1 | 桌面云台。 |
| WHEELED_BASE_DEVICE  | int | 2 | 轮式底座。 |
| POCKET_GIMBAL_CAMERA_DEVICE  | int | 3 | 口袋云台相机。 |