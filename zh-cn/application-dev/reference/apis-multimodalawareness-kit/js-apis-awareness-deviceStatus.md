# @ohos.multimodalAwareness.deviceStatus（设备状态感知）
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供对设备状态的感知能力。

> **说明：**
>
> 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

  ```ts
  import { deviceStatus } from '@kit.MultimodalAwarenessKit';
  ```

## SteadyStandingStatus

设备静止姿态感知状态（支架态）。

设备进入支架态指设备静止，且屏幕与水平面角度处于45度-135度。折叠屏手机需处于折叠状态或者完全展开状态。

**系统能力**：SystemCapability.MultimodalAwareness.DeviceStatus

| 名称                | 值   | 说明                   |
| ------------------- | ---- | ---------------------- |
| STATUS_EXIT  | 0    | 表示设备退出支架态。 |
| STATUS_ENTER | 1    | 表示设备进入支架态。 |

## deviceStatus.on('steadyStandingDetect')

 on(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void;

订阅设备静止姿态感知（支架态）事件。

**系统能力**：SystemCapability.MultimodalAwareness.DeviceStatus

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“steadyStandingDetect”，表示设备静止姿态（支架态）感知。 |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | 是   | 回调函数，返回设备静止姿态感知（支架态）状态信息。|

**错误码**：

以下错误码的详细介绍请参见[设备状态感知错误码](errorcode-deviceStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |
| 32500002 | Subscription failed. |

**示例**：

  ```ts
  try {
    deviceStatus.on('steadyStandingDetect', (data:deviceStatus.SteadyStandingStatus) => {
      console.info('now status = ' + data);
    });
  } catch (err) {
    console.info('on failed, err = ' + err);
  }
  ```

## deviceStatus.off('steadyStandingDetect')

off(type: 'steadyStandingDetect', callback?: Callback&lt;SteadyStandingStatus&gt;): void;

取消订阅设备静止姿态感知（支架态）事件。

**系统能力**：SystemCapability.MultimodalAwareness.DeviceStatus

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | 是   | 事件类型。type为“steadyStandingDetect”，表示设备静止姿态（支架态）感知。 |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | 否   | 回调函数，返回设备静止姿态感知（支架态）状态信息。|

**错误码**：

以下错误码的详细介绍请参见[设备状态感知错误码](errorcode-deviceStatus.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |
| 32500003 | Unsubscription failed. |

**示例**：

示例一：取消订阅该客户端订阅设备静止姿态感知（支架态）事件的所有回调。

  ```ts
  try {
    deviceStatus.off('steadyStandingDetect');
  } catch (err) {
    console.info('off failed, err = ' + err);
  }
  ```

示例二：取消订阅该客户端订阅设备静止姿态感知（支架态）事件的特定回调。

  ```ts
  import { Callback } from '@ohos.base';
  // 定义callback变量
  let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus.SteadyStandingStatus) => {
    console.info('now status = ' + data);
  };
  // 以callback为回调函数，订阅设备静止姿态感知（支架态）事件
  try {
    deviceStatus.on('steadyStandingDetect', callback);
  } catch (err) {
    console.info('on failed, err = ' + err);
  }
  // 取消该客户端订阅设备静止姿态感知（支架态）事件的特定回调函数
  try {
    deviceStatus.off('steadyStandingDetect', callback);
  } catch (err) {
    console.info('off failed, err = ' + err);
  }
  ```