# @ohos.bluetooth.access (蓝牙access模块)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块提供了打开和关闭蓝牙、获取蓝牙开关状态以及其他相关方法。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { access } from '@kit.ConnectivityKit';
```

## access.enableBluetooth

enableBluetooth(): void

开启蓝牙。

- 调用该接口时，系统弹出开启蓝牙的对话框，由用户确认是否需要开启蓝牙。如果应用想要感知用户操作对话框的行为，建议使用[access.enableBluetoothAsync](#accessenablebluetoothasync20)。
- 蓝牙开关状态结果可通过[access.on('stateChange')](#accessonstatechange)的回调函数获取到。
- 建议蓝牙开关状态是[STATE_OFF](#bluetoothstate)时，才调用该接口开启蓝牙（可使用[access.getState](#accessgetstate)判断当前蓝牙开关状态）。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息            |
| -------- | ------------------ |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001   | Service stopped.   |
|2900099   | Operation failed.  |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.enableBluetooth();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.enableBluetoothAsync<sup>20+</sup>

enableBluetoothAsync(): Promise&lt;void&gt;

开启蓝牙。使用Promise异步回调。
- 调用该接口时，系统弹出开启蓝牙的对话框，由用户确认是否需要开启蓝牙。应用可以感知用户操作对话框的行为。
- 蓝牙开关状态结果可通过[access.on('stateChange')](#accessonstatechange)的回调函数获取到。
- 建议蓝牙开关状态是[STATE_OFF](#bluetoothstate)时，才调用该接口开启蓝牙（可使用[access.getState](#accessgetstate)判断当前蓝牙开关状态）。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                | 说明                                   |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 201      | Permission denied.         |
| 801      | Capability not supported.  |
| 2900001  | Service stopped.           |
| 2900013  | The user does not respond. |
| 2900014  | User refuse the action.    |
| 2900099  | Operation failed.          |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.enableBluetoothAsync().then(() => {
        console.info('enableBluetoothAsync');
    }, (error: BusinessError) => {
        console.error('enableBluetoothAsync: errCode:' + error.code + ',errMessage' + error.message);
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.disableBluetooth

disableBluetooth(): void

关闭蓝牙。
- 调用该接口时，系统弹出关闭蓝牙的对话框，由用户确认是否需要关闭蓝牙。如果应用想要感知用户操作对话框的行为，建议使用[access.disableBluetoothAsync](#accessdisablebluetoothasync20)。
- 蓝牙开关状态结果可通过[access.on('stateChange')](#accessonstatechange)的回调函数获取到。
- 建议蓝牙开关状态是[STATE_ON](#bluetoothstate)时，才调用该接口关闭蓝牙（可使用[access.getState](#accessgetstate)判断当前蓝牙开关状态）。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

|错误码ID   | 错误信息           |
| -------- | ------------------ |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001   | Service stopped.   |
|2900099   | Operation failed.  |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.disableBluetooth();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.disableBluetoothAsync<sup>20+</sup>

disableBluetoothAsync(): Promise&lt;void&gt;

关闭蓝牙。使用Promise异步回调。
- 调用该接口时，系统弹出关闭蓝牙的对话框，由用户确认是否需要关闭蓝牙。应用可以感知用户操作对话框的行为。
- 蓝牙开关状态结果可通过[access.on('stateChange')](#accessonstatechange)的回调函数获取到。
- 建议蓝牙开关状态是[STATE_ON](#bluetoothstate)时，才调用该接口关闭蓝牙（可使用[access.getState](#accessgetstate)判断当前蓝牙开关状态）。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API**：从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                | 说明                                   |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 201      | Permission denied.         |
| 801      | Capability not supported.  |
| 2900001  | Service stopped.           |
| 2900013  | The user does not respond. |
| 2900014  | User refuse the action.    |
| 2900099  | Operation failed.          |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.disableBluetoothAsync().then(() => {
        console.info('disableBluetoothAsync');
    }, (error: BusinessError) => {
        console.error('disableBluetoothAsync: errCode:' + error.code + ',errMessage' + error.message);
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.getState

getState(): BluetoothState

获取蓝牙开关状态。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                              | 说明              |
| --------------------------------- | ---------------- |
| [BluetoothState](#bluetoothstate) | 表示蓝牙开关状态。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

|错误码ID   | 错误信息           |
| -------- | ------------------ |
|801 | Capability not supported.          |
|2900001   | Service stopped.   |
|2900099   | Operation failed.  |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let state = access.getState();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.on('stateChange')<a name="stateChange"></a>

on(type: 'stateChange', callback: Callback&lt;BluetoothState&gt;): void

订阅本端蓝牙开关状态变化事件。使用Callback异步回调。从API18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名   | 类型                                               | 必填  | 说明                                                       |
| -------- | ------------------------------------------------- | ----- | ---------------------------------------------------------- |
| type     | string                                            | 是    | 事件回调类型，支持的事件为'stateChange'，表示蓝牙开关状态变化事件。<br>如：当调用[access.enableBluetooth](#accessenablebluetooth)或[access.disableBluetooth](#accessdisablebluetooth)时，可触发该事件。               |
| callback | Callback&lt;[BluetoothState](#bluetoothstate)&gt; | 是    | 指定订阅的回调函数，会携带蓝牙开关状态。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

|错误码ID   | 错误信息           |
| -------- | ------------------ |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900099   | Operation failed.  |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

function onReceiveEvent(data: access.BluetoothState) {
    console.info('bluetooth state = '+ JSON.stringify(data));
}
try {
    access.on('stateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.off('stateChange')

off(type: 'stateChange', callback?: Callback&lt;BluetoothState&gt;): void

取消订阅本端蓝牙开关状态变化事件。从API18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。

**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | 是    | 事件回调类型，支持的事件为'stateChange'，表示蓝牙开关状态变化事件。           |
| callback | Callback&lt;[BluetoothState](#bluetoothstate)&gt; | 否    | 指定取消订阅的回调函数通知。<br>若传参，则需与[access.on('stateChange')](#accessonstatechange)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

function onReceiveEvent(data: access.BluetoothState) {
    console.info('bluetooth state = '+ JSON.stringify(data));
}
try {
    access.on('stateChange', onReceiveEvent);
    access.off('stateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## access.addPersistentDeviceId<sup>16+</sup>

addPersistentDeviceId(deviceId: string): Promise&lt;void&gt;

持久化存储蓝牙设备的虚拟MAC地址。
- 应用通过蓝牙相关接口，如扫描等途径获取到的设备地址（虚拟MAC地址）和实际的设备MAC地址不同。蓝牙子系统会保存一个虚拟MAC地址和实际设备MAC地址的映射关系。若应用想长期对该蓝牙设备进行操作使用，建议用此接口持久化存储该设备的虚拟MAC地址，后续可直接使用，该地址映射关系不会再改变。
- 指定持久化存储的虚拟MAC地址需是有效的（可使用[access.isValidRandomDeviceId](#accessisvalidrandomdeviceid16)判断）。
- 使用该接口时，开发者应确保该虚拟MAC地址对应的对端蓝牙设备实际地址是保持不变的，若对端设备实际地址发生变化，持久化存储的地址信息将失效，无法继续使用。
- 可调用[access.deletePersistentDeviceId](#accessdeletepersistentdeviceid16)删除已持久化存储的虚拟MAC地址。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

**原子化服务API**：从API version 16开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| deviceId     | string                                   | 是    | 对端设备的虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"。<br>该地址一般来源于蓝牙扫描结果，如：可通过调用[startScan](js-apis-bluetooth-ble.md#startscan15)或[connection.startBluetoothDiscovery](js-apis-bluetooth-connection.md#connectionstartbluetoothdiscovery)扫描得到。  |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900003 | Bluetooth disabled. |
|2900010 | The number of supported device addresses has reached the upper limit. |
|2900099 | Add persistent device address failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

let deviceId = '11:22:33:44:55:66'  // 该地址可通过BLE扫描获取
try {
    access.addPersistentDeviceId(deviceId);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## access.deletePersistentDeviceId<sup>16+</sup>

deletePersistentDeviceId(deviceId: string): Promise&lt;void&gt;

删除已持久化存储的蓝牙虚拟MAC地址。
- 该虚拟MAC地址通过[access.addPersistentDeviceId](#accessaddpersistentdeviceid16)持久化存储。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

**原子化服务API**：从API version 16开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| deviceId     | string                                   | 是    | 对端设备的虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"，<br>该地址一般来源于蓝牙扫描结果，如：通过调用[startScan](js-apis-bluetooth-ble.md#startscan15)或[connection.startBluetoothDiscovery](js-apis-bluetooth-connection.md#connectionstartbluetoothdiscovery)扫描得到。           |

**返回值：**

| 类型                            | 说明         |
| ----------------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900003 | Bluetooth disabled. |
|2900099 | delete persistent device address failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

let deviceId = '11:22:33:44:55:66'  // 该地址可通过BLE扫描获取
try {
    access.deletePersistentDeviceId(deviceId);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## access.getPersistentDeviceIds<sup>16+</sup>

getPersistentDeviceIds(): string[];

获取应用持久化存储过的蓝牙虚拟MAC地址。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

**原子化服务API**：从API version 16开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型                              | 说明              |
| --------------------------------- | ---------------- |
| string[] | 持久化存储过的蓝牙虚拟MAC地址列表。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900003 | Bluetooth disabled. |
|2900099 | Get persistent device address failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let deviceIds = access.getPersistentDeviceIds();
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## access.isValidRandomDeviceId<sup>16+</sup>

isValidRandomDeviceId(deviceId: string): boolean;

判断对端蓝牙设备的虚拟MAC地址是否有效。
- 有效的虚拟MAC地址一般来源于蓝牙扫描结果，如：通过调用[startScan](js-apis-bluetooth-ble.md#startscan15)或[connection.startBluetoothDiscovery](js-apis-bluetooth-connection.md#connectionstartbluetoothdiscovery)扫描得到。

**需要权限**：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API**：从API version 16开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名      | 类型                                       | 必填   | 说明                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| deviceId     | string                                   | 是    | 对端设备的虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"。           |

**返回值：**

| 类型                              | 说明              |
| --------------------------------- | ---------------- |
| boolean | 蓝牙设备的虚拟MAC地址是否是有效的。true表示有效地址，false表示无效地址。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[蓝牙服务子系统错误码](errorcode-bluetoothManager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900003 | Bluetooth disabled. |
|2900099 | Check persistent device address failed.                        |

**示例：**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let deviceId = '11:22:33:44:55:66'  // 该地址可通过BLE扫描获取
    let isValid = access.isValidRandomDeviceId(deviceId);
    console.info("isValid: " + isValid);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```

## BluetoothState

枚举，蓝牙开关状态。

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Communication.Bluetooth.Core

| 名称                    | 值  | 说明                 |
| --------------------- | ---- | ------------------ |
| STATE_OFF             | 0    | 表示蓝牙已关闭。          |
| STATE_TURNING_ON      | 1    | 表示蓝牙正在打开。          |
| STATE_ON              | 2    | 表示蓝牙已打开。           |
| STATE_TURNING_OFF     | 3    | 表示蓝牙正在关闭。          |
| STATE_BLE_TURNING_ON  | 4    | 表示蓝牙正在打开LE-only模式。 |
| STATE_BLE_ON          | 5    | 表示蓝牙正处于LE-only模式。  |
| STATE_BLE_TURNING_OFF | 6    | 表示蓝牙正在关闭LE-only模式。 |
