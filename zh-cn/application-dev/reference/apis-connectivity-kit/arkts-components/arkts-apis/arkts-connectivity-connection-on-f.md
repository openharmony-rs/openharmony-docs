# on

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## on('bluetoothDeviceFind')

```TypeScript
function on(type: 'bluetoothDeviceFind', callback: Callback<Array<string>>): void
```

订阅蓝牙设备扫描结果上报事件。使用Callback异步回调。

可扫描到的设备类型包括传统蓝牙设备和低功耗蓝牙设备。该上报方式只支持获取设备地址信息。推荐使用API version 18开始支持的[connection.on('discoveryResult')](#ondiscoveryresult)扫描上报方式，可获取到更多设备信息，包括设备地址、设备信号强度、设备名称和设备类型。

**起始版本：** 10

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本10-24：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bluetoothDeviceFind' | 是 | 事件回调类型，支持的事件为'bluetoothDeviceFind'，表示蓝牙设备扫描结果上报事件。当调用[connection.startBluetoothDiscovery](arkts-connectivity-connection-startbluetoothdiscovery-f.md)后，开始设备扫描，若扫描到设备，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 指定订阅的回调函数，会携带扫描到的设备地址集合。基于信息安全考虑，此处获取的设备地址为虚拟MAC地址。已配对的地址不会变更。若该设备重启蓝牙开关，重新获取到的虚拟地址会立即变更。若取消配对，蓝牙子系统会根据该地址的实际使用情况，决策后续变更时机；若其他应用正在使用该地址，则不会立刻变更。若要持久化保存该地址，可使用[access.addPersistentDeviceId](arkts-connectivity-access-addpersistentdeviceid-f.md)方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 10 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: Array<string>) { // data为蓝牙设备地址集合。
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('bluetoothDeviceFind', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## on('discoveryResult')

```TypeScript
function on(type: 'discoveryResult', callback: Callback<Array<DiscoveryResult>>): void
```

订阅蓝牙设备扫描结果上报事件。使用Callback异步回调。

可扫描到的设备类型包括传统蓝牙设备和低功耗蓝牙设备。该上报方式支持获取设备地址、设备信号强度、设备名称和设备类型。

**起始版本：** 18

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本18-24：ohos.permission.ACCESS_BLUETOOTH
- API版本12-17：ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'discoveryResult' | 是 | 事件回调类型，支持的事件为'discoveryResult'，表示蓝牙设备扫描结果上报事件。当调用[connection.startBluetoothDiscovery](arkts-connectivity-connection-startbluetoothdiscovery-f.md)后，开始设备扫描，若扫描到设备，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[DiscoveryResult](arkts-connectivity-connection-discoveryresult-i.md)&gt;&gt; | 是 | 指定订阅的回调函数，会携带扫描结果的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 12 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: Array<connection.DiscoveryResult>) => void = (data: Array<connection.DiscoveryResult>) => { // data为蓝牙设备扫描结果集合。
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('discoveryResult', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## on('bondStateChange')

```TypeScript
function on(type: 'bondStateChange', callback: Callback<BondStateParam>): void
```

订阅蓝牙配对状态变化事件。使用Callback异步回调。

**起始版本：** 10

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本10-24：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bondStateChange' | 是 | 事件回调类型，支持的事件为'bondStateChange'，表示蓝牙配对状态变化事件。当调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起主动配对，或者本机设备收到其他设备的配对请求时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BondStateParam](arkts-connectivity-connection-bondstateparam-i.md)&gt; | 是 | 指定订阅的回调函数，会携带配对状态结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 10 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.BondStateParam) { // data为回调函数入参，表示配对的状态。
    console.info('pair state = '+ JSON.stringify(data));
}
try {
    connection.on('bondStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## on('pinRequired')

```TypeScript
function on(type: 'pinRequired', callback: Callback<PinRequiredParam>): void
```

订阅配对请求事件。使用Callback异步回调。

**起始版本：** 10

**需要权限：** 
- API版本26+：ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API版本25：N/A
- API版本10-24：ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinRequired' | 是 | 事件回调类型，支持的事件为'pinRequired'，表示配对请求事件。当调用[connection.pairDevice](arkts-connectivity-connection-pairdevice-f.md)发起主动配对，或者本机设备收到其他设备的配对请求时，触发该事件。收到配对请求后，可调用[connection.setDevicePairingConfirmation](arkts-connectivity-connection-setdevicepairingconfirmation-f.md)确认或拒绝配对请求。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PinRequiredParam](arkts-connectivity-connection-pinrequiredparam-i.md)&gt; | 是 | 指定订阅的回调函数，会携带配对请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>**适用版本：** 10 - 24 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.PinRequiredParam) { // data为配对请求参数。
    console.info('pin required = '+ JSON.stringify(data));
}
try {
    connection.on('pinRequired', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## on('batteryChange')

```TypeScript
function on(type: 'batteryChange', callback: Callback<BatteryInfo>): void
```

订阅对端设备的电量信息变化事件。使用Callback异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'batteryChange' | 是 | 事件回调类型，支持的事件为'batteryChange'，表示对端设备的电量信息变化事件。当该设备通知电量变化时，会触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BatteryInfo](arkts-connectivity-connection-batteryinfo-i.md)&gt; | 是 | 指定订阅的回调函数，返回电量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: connection.BatteryInfo) => void = (data: connection.BatteryInfo) => {
    console.info('BatteryInfo = '+ JSON.stringify(data));
}
try {
    connection.on('batteryChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
