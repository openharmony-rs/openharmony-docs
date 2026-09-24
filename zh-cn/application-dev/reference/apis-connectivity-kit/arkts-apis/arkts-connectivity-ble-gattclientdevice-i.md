# GattClientDevice

```TypeScript
interface GattClientDevice
```

GATT客户端类，提供了和服务端进行连接和数据传输等操作方法。

使用该类的方法前，需通过[createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md)方法构造该类的实例。通过创建不同的该类实例，可以管理多路GATT连接。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): void
```

销毁client端实例。销毁后，通过[GattClientDevice](arkts-connectivity-ble-gattclientdevice-i.md)创建的实例将不可用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.close();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connect

```TypeScript
connect(): void
```

client端主动发起和server蓝牙设备的GATT协议连接。

远端设备地址已通过[createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md)方法中的deviceId参数指定。client可通过订阅[on('BLEConnectionStateChange')](#onbleconnectionstatechange)事件来感知连接是否成功。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.connect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## disconnect

```TypeScript
disconnect(): void
```

client断开与远端蓝牙低功耗设备的连接。

client可通过订阅[on('BLEConnectionStateChange')](#onbleconnectionstatechange)事件来感知断连是否成功。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.disconnect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getConnectedState

```TypeScript
getConnectedState(): ProfileConnectionState
```

获取当前与server端设备的连接状态。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md) | 蓝牙设备的profile连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    let result: ble.ProfileConnectionState = gattClient.getConnectedState();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getDeviceName

```TypeScript
getDeviceName(callback: AsyncCallback<string>): void
```

client获取server端设备名称。使用Callback异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当读取成功，err为undefined，data为server端设备名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { ble, constant } from '@kit.ConnectivityKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let gattClient: ble.GattClientDevice = ble.createGattClientDevice("11:22:33:44:55:66");
function ConnectStateChanged(state: ble.BLEConnectionChangeState) {
    console.info('bluetooth connect state changed');
    let connectState: ble.ProfileConnectionState = state.state;
    if (connectState == constant.ProfileConnectionState.STATE_CONNECTED) {
        gattClient.getDeviceName((err: BusinessError, data: string)=> {
            console.info('device name err ' + JSON.stringify(err));
            console.info('device name' + JSON.stringify(data));
        })
    }
}
// callback
try {
    gattClient.connect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="getdevicename-1"></a>

## getDeviceName

```TypeScript
getDeviceName(): Promise<string>
```

client获取server端设备名称。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，携带server端设备名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter.Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { ble, constant } from '@kit.ConnectivityKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let gattClient: ble.GattClientDevice = ble.createGattClientDevice("11:22:33:44:55:66");
gattClient.on('BLEConnectionStateChange', ConnectStateChanged);
function ConnectStateChanged(state: ble.BLEConnectionChangeState) {
    console.info('bluetooth connect state changed');
    let connectState: ble.ProfileConnectionState = state.state;
    if (connectState == constant.ProfileConnectionState.STATE_CONNECTED) {
        gattClient.getDeviceName().then((data: string) => {
            console.info('device name' + JSON.stringify(data));
        })
    }
}
// promise
try {
    gattClient.connect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getRssiValue

```TypeScript
getRssiValue(callback: AsyncCallback<number>): void
```

client端获取GATT连接链路信号强度 (Received Signal Strength Indication, RSSI)。使用Callback异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。获取链路信号强度成功，err为undefined，data为获取到的信号强度值，单位：dBm；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20 - 21 |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// callback
try {
    let gattClient: ble.GattClientDevice = ble.createGattClientDevice("XX:XX:XX:XX:XX:XX");
    gattClient.connect();
    let rssi = gattClient.getRssiValue((err: BusinessError, data: number)=> {
        console.info('rssi err ' + JSON.stringify(err));
        console.info('rssi value' + JSON.stringify(data));
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="getrssivalue-1"></a>

## getRssiValue

```TypeScript
getRssiValue(): Promise<number>
```

client端获取GATT连接链路信号强度 (Received Signal Strength Indication, RSSI)。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回链路的信号强度，单位：dBm。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20 - 21 |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    let gattClient: ble.GattClientDevice = ble.createGattClientDevice("XX:XX:XX:XX:XX:XX");
    gattClient.getRssiValue().then((data: number) => {
        console.info('rssi' + JSON.stringify(data));
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## getServices

```TypeScript
getServices(callback: AsyncCallback<Array<GattService>>): void
```

client获取server端支持的所有服务能力，即服务发现流程。使用Callback异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。应用调用该方法后，才能调用其他读写特征值、描述符等其他方法，且需确保server支持的服务能力中包含需要操作的特征值或描述符。包含接口如下所示：

readCharacteristicValue

[readDescriptorValue](#readdescriptorvalue)

writeCharacteristicValue

[writeDescriptorValue](#writedescriptorvalue)

setCharacteristicChangeNotification

setCharacteristicChangeIndication

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[GattService](arkts-connectivity-ble-gattservice-i.md)&gt;&gt; | 是 | 回调函数。当读取成功，err为undefined，data为server端的服务列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { ble, constant } from '@kit.ConnectivityKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// callback 模式。
let getServices = (code: BusinessError, gattServices: Array<ble.GattService>) => {
    if (code && code.code != 0) {
        console.info('bluetooth code is ' + code.code);
        return;
    }
    let services: Array<ble.GattService> = gattServices;
    console.info('bluetooth services size is ', services.length);
    for (let i = 0; i < services.length; i++) {
        console.info('bluetooth serviceUuid is ' + services[i].serviceUuid);
    }
}
let device: ble.GattClientDevice = ble.createGattClientDevice("11:22:33:44:55:66");
function ConnectStateChanged(state: ble.BLEConnectionChangeState) {
    console.info('bluetooth connect state changed');
    let connectState: ble.ProfileConnectionState = state.state;
    if (connectState == constant.ProfileConnectionState.STATE_CONNECTED) {
        device.getServices(getServices);
    }
}

try {
    device.connect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="getservices-1"></a>

## getServices

```TypeScript
getServices(): Promise<Array<GattService>>
```

client端获取server端支持的所有服务能力，即服务发现流程。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[GattService](arkts-connectivity-ble-gattservice-i.md)&gt;&gt; | Promise对象，返回获取到的server端服务列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { ble, constant } from '@kit.ConnectivityKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// Promise 模式。
let device: ble.GattClientDevice = ble.createGattClientDevice("11:22:33:44:55:66");
function ConnectStateChanged(state: ble.BLEConnectionChangeState) {
    console.info('bluetooth connect state changed');
    let connectState: ble.ProfileConnectionState = state.state;
    if (connectState == constant.ProfileConnectionState.STATE_CONNECTED) {
        device.getServices().then((result: Array<ble.GattService>) => {
            console.info('getServices successfully:' + JSON.stringify(result));
        });
    }
}
try {
    device.connect();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('BLECharacteristicChange')

```TypeScript
off(type: 'BLECharacteristicChange', callback?: Callback<BLECharacteristic>): void
```

client端取消订阅server端特征值变化事件。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLECharacteristicChange' | 是 | 事件回调类型，支持的事件为'BLECharacteristicChange'，表示server端特征值变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[on('BLECharacteristicChange')](#onblecharacteristicchange)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.off('BLECharacteristicChange');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('BLEConnectionStateChange')

```TypeScript
off(type: 'BLEConnectionStateChange', callback?: Callback<BLEConnectionChangeState>): void
```

client端取消订阅GATT profile协议的连接状态变化事件。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLEConnectionStateChange' | 是 | 事件回调类型，支持的事件为'BLEConnectionStateChange'，表示连接状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[on('BLEConnectionStateChange')](#onbleconnectionstatechange)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.off('BLEConnectionStateChange');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('BLEMtuChange')

```TypeScript
off(type: 'BLEMtuChange', callback?: Callback<number>): void
```

client端取消订阅MTU（最大传输单元）大小变更事件。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLEMtuChange' | 是 | 事件回调类型，支持的事件为'BLEMtuChange'，表示MTU大小变更事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与on('BLEMtuChange')中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.off('BLEMtuChange');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## off('serviceChange')

```TypeScript
off(type: 'serviceChange', callback?: Callback<void>): void
```

client端设备取消订阅server端设备服务变化的通知事件。

取消订阅后，server端设备服务变化，client端将不再收到事件通知。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceChange' | 是 | 事件回调类型，支持的事件为'serviceChange'，表示服务变化通知事件。当server端添加或删除服务时，会触发该事件通知client端。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 指定取消订阅服务变化的回调函数通知。若传参，则需与[on('serviceChange')](#onservicechange)中传入的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function ServiceChangedEvent() : void {
    console.info("service has changed.");
}

let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
// 需预先调用connect接口先连上server端设备
try {
    gattClient.off('serviceChange', ServiceChangedEvent);
} catch (err) {
    console.error(`errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
}
```

## offBlePhyUpdate

```TypeScript
offBlePhyUpdate(callback?: Callback<PhyValue>): void
```

取消订阅物理通道类型变更事件。使用Callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | 否 | 指定取消订阅的回调函数。若传参，则需与[onBlePhyUpdate](arkts-connectivity-ble-gattserver-i.md#onblephyupdate)中的回调函数一致，若无传参，则取消订阅所有物理通道类型变更的回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
function BlePhyCallback(data:ble.PhyValue) {
    console.info(`txPhy: ${data.txPhy}, rxPhy: ${data.rxPhy}`);
}
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    gattClient.offBlePhyUpdate(BlePhyCallback);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## on('BLECharacteristicChange')

```TypeScript
on(type: 'BLECharacteristicChange', callback: Callback<BLECharacteristic>): void
```

client端订阅server端特征值变化事件。使用Callback异步回调。

需调用setCharacteristicChangeNotification或者setCharacteristicChangeIndication，且启用通知或者指示能力后，才能接收到server端的特征值内容变更通知或者指示。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLECharacteristicChange' | 是 | 事件回调类型，支持的事件为'BLECharacteristicChange'，表示server端特征值变化事件。当client端收到server端特征值内容变更的通知或者指示时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt; | 是 | 指定订阅的回调函数，会携带server端变化后的特征值内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
function CharacteristicChange(characteristicChangeReq: ble.BLECharacteristic) {
    let serviceUuid: string = characteristicChangeReq.serviceUuid;
    let characteristicUuid: string = characteristicChangeReq.characteristicUuid;
    let value: Uint8Array = new Uint8Array(characteristicChangeReq.characteristicValue);
}
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.on('BLECharacteristicChange', CharacteristicChange);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## on('BLEConnectionStateChange')

```TypeScript
on(type: 'BLEConnectionStateChange', callback: Callback<BLEConnectionChangeState>): void
```

client端订阅GATT profile协议的连接状态变化事件。使用Callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLEConnectionStateChange' | 是 | 事件回调类型，支持的事件为'BLEConnectionStateChange'，表示连接状态变化事件。client和server端之间的连接状态发生变化时，触发该事件。当client端调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)或[disconnect](arkts-connectivity-ble-gattserver-i.md#disconnect)时，可能引起连接状态发生变化。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md)&gt; | 是 | 指定订阅的回调函数，会携带连接状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
function ConnectStateChanged(state: ble.BLEConnectionChangeState) {
    console.info('bluetooth connect state changed');
    let connectState: ble.ProfileConnectionState = state.state;
}
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.on('BLEConnectionStateChange', ConnectStateChanged);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## on('BLEMtuChange')

```TypeScript
on(type: 'BLEMtuChange', callback: Callback<number>): void
```

client端订阅MTU（最大传输单元）大小变更事件。使用Callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BLEMtuChange' | 是 | 事件回调类型，支持的事件为'BLEMtuChange'，表示MTU大小变更事件。当调用[setBLEMtuSize](#setblemtusize)方法，client端发起MTU大小协商后，会触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 指定订阅的回调函数，会携带协商后的MTU大小。单位：Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    gattClient.on('BLEMtuChange', (mtu: number) => {
      console.info('BLEMtuChange, mtu: ' + mtu);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## on('serviceChange')

```TypeScript
on(type: 'serviceChange', callback: Callback<void>): void
```

client端设备订阅server端设备服务变化的通知事件，使用Callback异步回调。

如client端已订阅该事件，当server端添加或删除服务时，client端均会收到服务变化通知。client端收到服务变化通知时，建议重新调用[getServices](#getservices)获取server端设备支持的最新服务能力。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'serviceChange' | 是 | 事件回调类型，支持的事件为'serviceChange'，表示服务变化通知事件。当server端添加或删除服务时，会触发该事件通知client端。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 通知client端设备，server端服务已发生变更。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function ServiceChangedEvent() : void {
    console.info("service has changed.");
}

let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
// 需预先调用connect接口先连上server端设备
try {
    gattClient.on('serviceChange', ServiceChangedEvent);
} catch (err) {
    console.error(`errCode: ${(err as BusinessError).code}, errMessage: ${(err as BusinessError).message}`);
}
```

## onBlePhyUpdate

```TypeScript
onBlePhyUpdate(callback: Callback<PhyValue>): void
```

订阅物理通道类型变更事件。使用Callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | 是 | 指定订阅的回调函数，会携带变更后最新的物理通道类型。当本端server调用[setPhy](arkts-connectivity-ble-gattserver-i.md#setphy)或对端变更当前物理通道类型后，如订阅此事件，均会收到携带最新物理通道类型的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |

**示例**

```TypeScript
function BlePhyCallback(data:ble.PhyValue) {
    console.info(`txPhy: ${data.txPhy}, rxPhy: ${data.rxPhy}`);
}
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    gattClient.onBlePhyUpdate(BlePhyCallback);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## readCharacteristicValue

```TypeScript
readCharacteristicValue(characteristic: BLECharacteristic, callback: AsyncCallback<BLECharacteristic>): void
```

client端从指定的server端特征值读取数据。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参特征值UUID；否则会读取失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。读取特征值过程中，需确保[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)入参特征值的serviceUuid、characteristicUuid准确。characteristicValue表示的数据内容长度可由用户任意指定，不会影响实际读取到的特征值数据内容。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要读取的特征值。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt; | 是 | 回调函数。当读取成功，err为undefined，data为获取到的特征值对象，包含读取到的数据内容；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901000](../errorcode-bluetoothManager.md#2901000-禁止读操作) | Read forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
function readCcc(code: BusinessError, BLECharacteristic: ble.BLECharacteristic) {
  if (code.code != 0) {
      return;
  }
  console.info('bluetooth characteristic uuid: ' + BLECharacteristic.characteristicUuid);
  let value = new Uint8Array(BLECharacteristic.characteristicValue);
  console.info('bluetooth characteristic value: ' + value[0]);
}

let descriptors: Array<ble.BLEDescriptor> = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
characteristicValue: bufferCCC, descriptors:descriptors};

try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.readCharacteristicValue(characteristic, readCcc);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="readcharacteristicvalue-1"></a>

## readCharacteristicValue

```TypeScript
readCharacteristicValue(characteristic: BLECharacteristic): Promise<BLECharacteristic>
```

client端从指定的server端特征值读取数据。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参特征值UUID；否则会读取失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。读取特征值过程中，需确保[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)入参特征值的serviceUuid、characteristicUuid准确。characteristicValue表示的数据内容长度可由用户任意指定，不会影响实际读取到的特征值数据内容。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要读取的特征值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)&gt; | Promise对象，返回获取到的特征值对象，包含读取到的数据内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901000](../errorcode-bluetoothManager.md#2901000-禁止读操作) | Read forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let descriptors: Array<ble.BLEDescriptor> = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
characteristicValue: bufferCCC, descriptors:descriptors};

try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.readCharacteristicValue(characteristic);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## readDescriptorValue

```TypeScript
readDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback<BLEDescriptor>): void
```

client端从指定的server端描述符读取数据。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参描述符UUID；否则会读取失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。读取描述符过程中，需确保[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)入参描述符的serviceUuid、characteristicUuid、descriptorUuid准确。descriptorValue表示的数据内容长度可由用户任意指定，不会影响实际读取到的描述符数据内容。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | 是 | 需要读取的描述符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)&gt; | 是 | 回调函数。当读取成功，err为undefined，data为获取到的描述符对象，包含读取到的数据内容；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901000](../errorcode-bluetoothManager.md#2901000-禁止读操作) | Read forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
function readDesc(code: BusinessError, BLEDescriptor: ble.BLEDescriptor) {
    if (code.code != 0) {
        return;
    }
    console.info('bluetooth descriptor uuid: ' + BLEDescriptor.descriptorUuid);
    let value = new Uint8Array(BLEDescriptor.descriptorValue);
    console.info('bluetooth descriptor value: ' + value[0]);
}

let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB',
    descriptorValue: bufferDesc
};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.readDescriptorValue(descriptor, readDesc);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="readdescriptorvalue-1"></a>

## readDescriptorValue

```TypeScript
readDescriptorValue(descriptor: BLEDescriptor): Promise<BLEDescriptor>
```

client端从指定的server端描述符读取数据。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参描述符UUID；否则会读取失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。读取描述符过程中，需确保[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)入参描述符的serviceUuid、characteristicUuid、descriptorUuid准确。descriptorValue表示的数据内容长度可由用户任意指定，不会影响实际读取到的描述符数据内容。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | 是 | 需要读取的描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md)&gt; | Promise对象，返回获取到的描述符对象，包含读取到的数据内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901000](../errorcode-bluetoothManager.md#2901000-禁止读操作) | Read forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB',
    descriptorValue: bufferDesc
};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.readDescriptorValue(descriptor);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## readPhy

```TypeScript
readPhy(): Promise<PhyValue>
```

获取client端连接链路的物理通道类型。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法发起连接，并等待连接成功后，再调用该方法。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PhyValue](arkts-connectivity-ble-phyvalue-i.md)&gt; | Promise对象，返回client端连接链路的物理通道类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established. |

**示例**

```TypeScript
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    gattClient.readPhy().then((phyValue:ble.PhyValue) => {
        console.info(`txPhy: ${phyValue.txPhy}, rxPhy: ${phyValue.rxPhy}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## setBLEMtu

```TypeScript
setBLEMtu(mtu: number): Promise<number>
```

client端同server端协商MTU（最大传输单元）大小。与[setBLEMtuSize](#setblemtusize)相比，本接口直接通过Promise返回实际协商成功的MTU结果，无需额外订阅on('BLEMtuChange')事件获取协商结果。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。需保证入参符合取值范围，不在取值范围内会直接返回异常。如果未协商，MTU大小默认为23字节。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mtu | number | 是 | 需要协商的mtu大小，取值范围：[23, 517]，单位：Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回实际协商成功的Mtu结果，单位：Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established. |

**示例**

```TypeScript
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.setBLEMtu(128).then(outMtuSize => {
        console.info('实际设置的mtu：' + outMtuSize);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## setBLEMtuSize

```TypeScript
setBLEMtuSize(mtu: number): void
```

client端同server端协商MTU（最大传输单元）大小。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。通过on('BLEMtuChange')，订阅MTU协商结果。如果未协商，MTU大小默认为23字节。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mtu | number | 是 | 需要协商的mtu大小，取值范围：[23, 517]，单位：Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.setBLEMtuSize(128);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## setCharacteristicChangeIndication

```TypeScript
setCharacteristicChangeIndication(
      characteristic: BLECharacteristic,
      enable: boolean,
      callback: AsyncCallback<void>
    ): void
```

client端启用或者禁用接收server端特征值内容变更指示的能力。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且需包含指定的入参特征值UUID。server端对应的特征值需包含标准协议定义的Client Characteristic Configuration描述符UUID（00002902-0000-1000-8000-00805f9b34fb），server端才能支持发送变更指示。若启用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，启用server端的指示能力。若禁用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，禁用server端的指示能力。通过[on('BLECharacteristicChange')](#onblecharacteristicchange)接收server端特征值内容变更指示。若client端收到server端特征值内容变更指示后，系统蓝牙服务会主动回复确认，应用无需关注。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要管理的server端特征值。 |
| enable | boolean | 是 | 是否启用接收server端特征值指示的能力。true表示启用，false表示禁用。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// 创建descriptors。
let descriptors: Array<ble.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(2);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;
let arrayBufferC = new ArrayBuffer(8);
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
try {
  let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
  device.setCharacteristicChangeIndication(characteristic, false, (err: BusinessError) => {
    if (err) {
      console.error('notifyCharacteristicChanged callback failed');
    } else {
      console.info('notifyCharacteristicChanged callback successful');
    }
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="setcharacteristicchangeindication-1"></a>

## setCharacteristicChangeIndication

```TypeScript
setCharacteristicChangeIndication(characteristic: BLECharacteristic, enable: boolean): Promise<void>
```

client端启用或者禁用接收server端特征值内容变更指示的能力。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且需包含指定的入参特征值UUID。server端对应的特征值需包含标准协议定义的Client Characteristic Configuration描述符UUID（00002902-0000-1000-8000-00805f9b34fb），server端才能支持发送变更指示。若启用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，启用server端的指示能力。若禁用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，禁用server端的指示能力。通过[on('BLECharacteristicChange')](#onblecharacteristicchange)接收server端特征值内容变更指示。若client端收到server端特征值内容变更指示后，系统蓝牙服务会主动回复确认，应用无需关注。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要管理的server端特征值。 |
| enable | boolean | 是 | 是否启用接收server端特征值指示的能力。true表示启用，false表示禁用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// 创建descriptors。
let descriptors: Array<ble.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(2);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;
let arrayBufferC = new ArrayBuffer(8);
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
try {
  let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
  device.setCharacteristicChangeIndication(characteristic, false);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## setCharacteristicChangeNotification

```TypeScript
setCharacteristicChangeNotification(
      characteristic: BLECharacteristic,
      enable: boolean,
      callback: AsyncCallback<void>
    ): void
```

client端启用或者禁用接收server端特征值内容变更通知的能力。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且需包含指定的入参特征值UUID。server端对应的特征值需包含标准协议定义的Client Characteristic Configuration描述符UUID（00002902-0000-1000-8000-00805f9b34fb），server端才能支持发送变更通知。若启用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，启用server端的通知能力。若禁用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，禁用server端的通知能力。通过[on('BLECharacteristicChange')](#onblecharacteristicchange)接收server端特征值内容变更通知。若client端收到server端特征值内容变更通知后，无需回复确认。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要管理的server端特征值。 |
| enable | boolean | 是 | 是否启用接收server端特征值通知的能力。true表示启用，false表示禁用。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当调用成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// 创建descriptors。
let descriptors: Array<ble.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(2);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;
let arrayBufferC = new ArrayBuffer(8);
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.setCharacteristicChangeNotification(characteristic, false, (err: BusinessError) => {
        if (err) {
            console.error('notifyCharacteristicChanged callback failed');
        } else {
            console.info('notifyCharacteristicChanged callback successful');
        }
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="setcharacteristicchangenotification-1"></a>

## setCharacteristicChangeNotification

```TypeScript
setCharacteristicChangeNotification(characteristic: BLECharacteristic, enable: boolean): Promise<void>
```

client端启用或者禁用接收server端特征值内容变更通知的能力。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且需包含指定的入参特征值UUID。server端对应的特征值需包含标准协议定义的Client Characteristic Configuration描述符UUID（00002902-0000-1000-8000-00805f9b34fb），server端才能支持发送变更通知。若启用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，启用server端的通知能力。若禁用该能力，系统蓝牙服务会自动往server端写Client Characteristic Configuration描述符，禁用server端的通知能力。通过[on('BLECharacteristicChange')](#onblecharacteristicchange)接收server端特征值内容变更通知。若client端收到server端特征值内容变更通知后，无需回复确认。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要管理的server端特征值。 |
| enable | boolean | 是 | 是否启用接收server端特征值通知的能力。true表示启用，false表示禁用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
// 创建descriptors。
let descriptors: Array<ble.BLEDescriptor> = [];
let arrayBuffer = new ArrayBuffer(2);
let descV = new Uint8Array(arrayBuffer);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: arrayBuffer};
descriptors[0] = descriptor;
let arrayBufferC = new ArrayBuffer(8);
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB', characteristicValue: arrayBufferC, descriptors:descriptors};
try {
  let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
  device.setCharacteristicChangeNotification(characteristic, false);
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## setPhy

```TypeScript
setPhy(phyValue: PhyValue): Promise<void>
```

client端设置连接链路的物理通道类型。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法发起连接，并等待连接成功后，再调用该方法。本端client调用setPhy设置物理通道类型后，底层会根据对端设备能力，协商出本端和对端设备均支持的物理通道类型作为最终结果。例如本端支持并设置[BLE_PHY_2M](arkts-connectivity-ble-blephy-e.md)，但对端设备仅支持[BLE_PHY_1M](arkts-connectivity-ble-blephy-e.md)，则最终设置的结果仍为[BLE_PHY_1M](arkts-connectivity-ble-blephy-e.md)。协商后的最终物理通道类型可通过订阅[onBlePhyUpdate](arkts-connectivity-ble-gattserver-i.md#onblephyupdate)事件获取。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phyValue | [PhyValue](arkts-connectivity-ble-phyvalue-i.md) | 是 | 连接链路的物理通道类型配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established. |

**示例**

```TypeScript
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    let phyValue: ble.PhyValue = {
        txPhy: ble.BlePhy.BLE_PHY_1M,
        rxPhy: ble.BlePhy.BLE_PHY_1M
    }
    gattClient.setPhy(phyValue);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## updateConnectionParam

```TypeScript
updateConnectionParam(param: ConnectionParam): Promise<void>
```

向对端设备发起连接参数更新请求，调用成功后可以切换与对端数据传输速度。使用Promise异步回调。

需先调用[connect](arkts-connectivity-ble-gattserver-i.md#connect)方法，等GATT profile连接成功后才能使用。不调用该接口时，默认连接参数类型为[ble.ConnectionParam.BALANCED](arkts-connectivity-ble-connectionparam-e.md)。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [ConnectionParam](arkts-connectivity-ble-connectionparam-e.md) | 是 | 连接参数类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let gattClient: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
try {
    gattClient.updateConnectionParam(ble.ConnectionParam.LOW_POWER);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## writeCharacteristicValue

```TypeScript
writeCharacteristicValue(
      characteristic: BLECharacteristic,
      writeType: GattWriteType,
      callback: AsyncCallback<void>
    ): void
```

client端向指定的server端特征值写入数据。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参特征值UUID；否则会写入失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。应用单次可写入的特征值数据长度限制为（MTU-3）字节。调用方可根据实际需要通过[setBLEMtuSize](#setblemtusize)接口指定MTU大小，进而修改单次可写入的特征值数据长度。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要写入的特征值，包含写入的数据内容。 |
| writeType | [GattWriteType](arkts-connectivity-ble-gattwritetype-e.md) | 是 | 写入特征值的方式。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当写入成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901001](../errorcode-bluetoothManager.md#2901001-禁止写操作) | Write forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let descriptors: Array<ble.BLEDescriptor> = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  characteristicValue: bufferCCC, descriptors:descriptors};
function writeCharacteristicValueCallBack(code: BusinessError) {
    if (code != null) {
        return;
    }
    console.info('bluetooth writeCharacteristicValue success');
}
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeCharacteristicValue(characteristic, ble.GattWriteType.WRITE, writeCharacteristicValueCallBack);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="writecharacteristicvalue-1"></a>

## writeCharacteristicValue

```TypeScript
writeCharacteristicValue(characteristic: BLECharacteristic, writeType: GattWriteType): Promise<void>
```

client端向指定的server端特征值写入数据。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参特征值UUID；否则会写入失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。应用单次可写入的特征值数据长度限制为（MTU-3）字节。调用方可根据实际需要通过[setBLEMtuSize](#setblemtusize)接口指定MTU大小，进而修改单次可写入的特征值数据长度。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| characteristic | [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | 是 | 需要写入的特征值，包含写入的数据内容。 |
| writeType | [GattWriteType](arkts-connectivity-ble-gattwritetype-e.md) | 是 | 写入特征值的方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901001](../errorcode-bluetoothManager.md#2901001-禁止写操作) | Write forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let descriptors: Array<ble.BLEDescriptor>  = [];
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB', descriptorValue: bufferDesc};
descriptors[0] = descriptor;

let bufferCCC = new ArrayBuffer(8);
let cccV = new Uint8Array(bufferCCC);
cccV[0] = 1;
let characteristic: ble.BLECharacteristic = {serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
  characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
  characteristicValue: bufferCCC, descriptors:descriptors};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeCharacteristicValue(characteristic, ble.GattWriteType.WRITE);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## writeDescriptorValue

```TypeScript
writeDescriptorValue(descriptor: BLEDescriptor, callback: AsyncCallback<void>): void
```

client端向指定的server端描述符写入数据。使用Callback异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参描述符UUID；否则会写入失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。应用单次可写入的描述符数据长度限制为（MTU-3）字节。调用方可根据实际需要通过[setBLEMtuSize](#setblemtusize)接口指定MTU大小，进而修改单次可写入的描述符数据长度。Client Characteristic Configuration描述符（UUID：00002902-0000-1000-8000-00805f9b34fb）和 Server Characteristic Configuration描述符（UUID：00002903-0000-1000-8000-00805f9b34fb）较为特殊，蓝牙标准协议规定内容长度为2字节，写入内容长度应设置为2字节。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | 是 | 需要写入的描述符，包含写入的数据内容。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当写入成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901001](../errorcode-bluetoothManager.md#2901001-禁止写操作) | Write forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB',
    descriptorValue: bufferDesc
};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeDescriptorValue(descriptor, (err: BusinessError) => {
        if (err) {
            console.error('writeDescriptorValue callback failed');
        } else {
            console.info('writeDescriptorValue callback successful');
        }
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

<a id="writedescriptorvalue-1"></a>

## writeDescriptorValue

```TypeScript
writeDescriptorValue(descriptor: BLEDescriptor): Promise<void>
```

client端向指定的server端描述符写入数据。使用Promise异步回调。

需要先调用[getServices](#getservices)，获取到server端所有支持的能力，且包含指定的入参描述符UUID；否则会写入失败。异步回调结果返回后，才能调用下一次读取或者写入操作，如readCharacteristicValue、[readDescriptorValue](#readdescriptorvalue)、writeCharacteristicValue、[writeDescriptorValue](#writedescriptorvalue)、setCharacteristicChangeNotification和setCharacteristicChangeIndication。应用单次可写入的描述符数据长度限制为（MTU-3）字节。调用方可根据实际需要通过[setBLEMtuSize](#setblemtusize)接口指定MTU大小，进而修改单次可写入的描述符数据长度。Client Characteristic Configuration描述符（UUID：00002902-0000-1000-8000-00805f9b34fb）和 Server Characteristic Configuration描述符（UUID：00002903-0000-1000-8000-00805f9b34fb）较为特殊，蓝牙标准协议规定内容长度为2字节，写入内容长度应设置为2字节。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | 是 | 需要写入的描述符，包含写入的数据内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900011](../errorcode-bluetoothManager.md#2900011-操作频繁) | The operation is busy. The last operation is not complete.<br>**适用版本：** 20+ |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901001](../errorcode-bluetoothManager.md#2901001-禁止写操作) | Write forbidden. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | The connection is not established.<br>**适用版本：** 20+ |
| [2901004](../errorcode-bluetoothManager.md#2901004-gatt传输拥塞) | The connection is congested.<br>**适用版本：** 20+ |
| [2901005](../errorcode-bluetoothManager.md#2901005-gatt未加密) | The connection is not encrypted.<br>**适用版本：** 20+ |
| [2901006](../errorcode-bluetoothManager.md#2901006-gatt未认证) | The connection is not authenticated.<br>**适用版本：** 20+ |
| [2901007](../errorcode-bluetoothManager.md#2901007-gatt未授权) | The connection is not authorized.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
let bufferDesc = new ArrayBuffer(2);
let descV = new Uint8Array(bufferDesc);
descV[0] = 0; // 以Client Characteristic Configuration描述符为例，表示bit0、bit1均为0，notification和indication均不开启
let descriptor: ble.BLEDescriptor = {
    serviceUuid: '00001810-0000-1000-8000-00805F9B34FB',
    characteristicUuid: '00001820-0000-1000-8000-00805F9B34FB',
    descriptorUuid: '00002902-0000-1000-8000-00805F9B34FB',
    descriptorValue: bufferDesc
};
try {
    let device: ble.GattClientDevice = ble.createGattClientDevice('XX:XX:XX:XX:XX:XX');
    device.writeDescriptorValue(descriptor).then(() => {
        console.info('writeDescriptorValue promise success');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
