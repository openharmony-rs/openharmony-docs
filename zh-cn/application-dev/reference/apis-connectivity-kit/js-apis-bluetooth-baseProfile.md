# @ohos.bluetooth.baseProfile (蓝牙baseProfile模块)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块提供不同的蓝牙技术协议的基础公共方法。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { baseProfile } from '@kit.ConnectivityKit';
```
## BaseProfile

基础Profile接口定义，提供订阅和获取连接状态等公共能力。如：[A2dpSourceProfile](js-apis-bluetooth-a2dp.md#a2dpsourceprofile)、[HandsFreeAudioGatewayProfile](js-apis-bluetooth-hfp.md#handsfreeaudiogatewayprofile)等[Profile](../../connectivity/terminology.md#profile)类型都继承于该类。

## ProfileConnectionState

type ProfileConnectionState = constant.ProfileConnectionState

本端和对端蓝牙设备间的Profile连接状态。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 类型                  | 说明                  |
| ------------------- | ------------------- |
| [constant.ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | 本端和对端蓝牙设备间的Profile连接状态。 |

## StateChangeParam

本端和对端蓝牙设备间Profile连接状态变化参数。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称     | 类型                           | 只读 | 可选 | 说明                            |
| -------- | ----------------------------- | ---- | ---- | ------------------------------- |
| deviceId | string                        | 否   | 否   | 对端设备地址，例如："XX:XX:XX:XX:XX:XX"。   |
| state    | [ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate)        | 否   | 否   | Profile连接状态。 |
| cause<sup>12+</sup>| [DisconnectCause](#disconnectcause12) | 否 | 否 | Profile断开连接的原因。|

## DisconnectCause<sup>12+</sup>

枚举，Profile断开连接的原因。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称                 | 值  | 说明     |
| ------------------ | ---- | ------ |
| USER_DISCONNECT            | 0    | 用户主动断开连接。|
| CONNECT_FROM_KEYBOARD      | 1    | 连接请求需从键盘侧发起。|
| CONNECT_FROM_MOUSE         | 2    | 连接请求需从鼠标侧发起。|
| CONNECT_FROM_CAR           | 3    | 连接请求需从车机侧发起。|
| TOO_MANY_CONNECTED_DEVICES | 4    | 当前连接数量超过上限。|
| CONNECT_FAIL_INTERNAL      | 5    | 内部错误。|

## BaseProfile.getConnectedDevices

getConnectedDevices(): Array&lt;string&gt;

获取和本端设备间已连接Profile的对端设备列表。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                  | 说明                  |
| ------------------- | ------------------- |
| Array&lt;string&gt; | 返回已连接Profile的对端设备列表。<br>基于信息安全考虑，此处获取的设备地址为虚拟MAC地址。<br>- 已配对的地址不会变更。<br>- 若取消配对该设备或蓝牙关闭后，再次重新获取，该虚拟地址会变更。<br>- 若要持久化保存该地址，可使用[access.addPersistentDeviceId](js-apis-bluetooth-access.md#accessaddpersistentdeviceid16)方法。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';

try {
    let a2dpSrc = a2dp.createA2dpSrcProfile(); // 以a2dp举例
    let retArray = a2dpSrc.getConnectedDevices();
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```

## BaseProfile.getConnectionState

getConnectionState(deviceId: string): ProfileConnectionState

获取和对端设备间Profile的连接状态。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名    | 类型     | 必填   | 说明      |
| ------ | ------ | ---- | ------- |
| deviceId | string | 是    | 对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型                                              | 说明                    |
| ------------------------------------------------- | ----------------------- |
| [ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | 返回Profile的连接状态。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';

try {
    let a2dpSrc = a2dp.createA2dpSrcProfile(); // 以a2dp举例
    let ret = a2dpSrc.getConnectionState('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## BaseProfile.on('connectionStateChange')

on(type: 'connectionStateChange', callback: Callback&lt;StateChangeParam&gt;): void

订阅Profile的连接状态变化事件。使用Callback异步回调。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | 是    | 事件回调类型，支持的事件为'connectionStateChange'，表示Profile连接状态变化事件。<br>当Profile连接状态变化时，触发该事件。 |
| callback | Callback&lt;[StateChangeParam](#statechangeparam)&gt; | 是    | 指定订阅的回调函数，会携带Profile连接状态。                        |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';

function onReceiveEvent(data: baseProfile.StateChangeParam) {
    console.info('a2dp state = '+ JSON.stringify(data));
}
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile(); // 以a2dp举例
    a2dpSrc.on('connectionStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## BaseProfile.off('connectionStateChange')

off(type: 'connectionStateChange', callback?: Callback&lt;[StateChangeParam](#statechangeparam)&gt;): void

取消订阅Profile的连接状态变化事件。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | 是    | 事件回调类型，支持的事件为'connectionStateChange'，表示Profile连接状态变化事件。 |
| callback | Callback&lt;[StateChangeParam](#statechangeparam)&gt; | 否    | 指定取消订阅的回调函数通知。<br>若传参，则需与[BaseProfile.on('connectionStateChange')](#baseprofileonconnectionstatechange)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。                               |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';

function onReceiveEvent(data: baseProfile.StateChangeParam) {
    console.info('a2dp state = '+ JSON.stringify(data));
}
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile(); // 以a2dp举例
    a2dpSrc.on('connectionStateChange', onReceiveEvent);
    a2dpSrc.off('connectionStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```