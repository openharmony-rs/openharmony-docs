# HidDeviceProfile

该实例表示蓝牙HID通信中的HID Device角色。

该类继承于[BaseProfile](arkts-connectivity-hid-baseprofile-t.md)，因此可以使用其父类中的方法。使用该类的方法前，需通过[createHidDeviceProfile](arkts-connectivity-hid-createhiddeviceprofile-f.md)方法构造该类的实例。通过该实例可以操作设备端的行为，如注册HID设备（[registerHidDevice](#registerhiddevice)），发送报告（[sendReport](#sendreport)）等。和该实例角色相对应的是HID Host。

**继承/实现关系：** HidDeviceProfile extends [BaseProfile](arkts-connectivity-hid-baseprofile-t.md)

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
connect(deviceId: BluetoothAddress): void
```

向指定的HID主机发起连接。

调用该接口前需要先调用[registerHidDevice](#registerhiddevice)完成HID设备能力注册。可通过订阅[on('connectionStateChange')](../../../reference/apis-connectivity-kit/js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange)事件来感知连接是否成功。当不需要连接时需调用[disconnect](#disconnect)断开连接。此外，调用[unregisterHidDevice](#unregisterhiddevice)解除注册也会断开已有的HID主机连接。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | [BluetoothAddress](arkts-connectivity-hid-bluetoothaddress-t.md) | 是 | 需要连接的对端蓝牙设备地址信息，HID设备中不涉及rawAddressType，无需给定该参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Remote Device profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903052](../errorcode-bluetoothManager.md#2903052-hid未注册) | App not register. |

**示例**

```TypeScript
import { common } from '@kit.ConnectivityKit';

let device: common.BluetoothAddress = {
    "address": "11:22:33:44:55:66",
    "addressType": common.BluetoothAddressType.REAL,
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.connect(device);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## disconnect

```TypeScript
disconnect(): void
```

断开与当前HID主机的连接，并释放相关的资源。

调用成功后不影响当前HID设备的注册状态，应用仍处于已注册状态，可以再次调用[connect](#connect)连接新的HID主机。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903052](../errorcode-bluetoothManager.md#2903052-hid未注册) | App not register. |

**示例**

```TypeScript
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.disconnect();
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## offGetReport

```TypeScript
offGetReport(callback?: Callback<GetReportData>): void
```

取消订阅主机向HID设备发出的GET_REPORT传输请求事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GetReportData](arkts-connectivity-hid-getreportdata-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[onGetReport](#ongetreport)中的回调函数一致；若无传参，则取消订阅所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.GetReportData) {
    console.info(`type: ${callback.type}, id: ${callback.id}, bufferSize: ${callback.bufferSize}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onGetReport(onReceiveEvent);
    hidDevice.offGetReport(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## offInterruptDataReceived

```TypeScript
offInterruptDataReceived(callback?: Callback<InterruptData>): void
```

取消订阅主机通过中断传输通道发送数据事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterruptData](arkts-connectivity-hid-interruptdata-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[onInterruptDataReceived](#oninterruptdatareceived)中的回调函数一致；若无传参，则取消订阅所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.InterruptData) {
    console.info(`id: ${callback.id}, dataSize: ${callback.data.length}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onInterruptDataReceived(onReceiveEvent);
    hidDevice.offInterruptDataReceived(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## offSetProtocol

```TypeScript
offSetProtocol(callback?: Callback<ProtocolData>): void
```

取消订阅主机向HID设备发送的SET_PROTOCOL请求事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProtocolData](arkts-connectivity-hid-protocoldata-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[onSetProtocol](#onsetprotocol)中的回调函数一致；若无传参，则取消订阅所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.ProtocolData) {
    console.info(`protocol: ${callback.protocol}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onSetProtocol(onReceiveEvent);
    hidDevice.offSetProtocol(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## offSetReport

```TypeScript
offSetReport(callback?: Callback<SetReportData>): void
```

取消订阅主机向HID设备发出的SET_REPORT传输请求事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SetReportData](arkts-connectivity-hid-setreportdata-i.md)&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[onSetReport](#onsetreport)中的回调函数一致；若无传参，则取消订阅所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.SetReportData) {
    console.info(`type: ${callback.type}, id: ${callback.id}, dataSize: ${callback.data.length}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onSetReport(onReceiveEvent);
    hidDevice.offSetReport(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## offVirtualCableUnplug

```TypeScript
offVirtualCableUnplug(callback?: Callback<void>): void
```

取消订阅主机断开HID虚拟链路事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[onVirtualCableUnplug](#onvirtualcableunplug)中的回调函数一致；若无传参，则取消订阅所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent() {
    console.info(`onVirtualCableUnplug`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onVirtualCableUnplug(onReceiveEvent);
    hidDevice.offVirtualCableUnplug(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## onGetReport

```TypeScript
onGetReport(callback: Callback<GetReportData>): void
```

订阅HID主机向HID设备发送的GET_REPORT传输请求事件，使用callback异步回调。收到回调后可以通过调用接口[replyReport](#replyreport)进行回复。当收到的数据不符合预期时，可以通过调用接口[reportError](#reporterror)进行回复。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GetReportData](arkts-connectivity-hid-getreportdata-i.md)&gt; | 是 | 回调函数，返回收到的报告数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.GetReportData) {
    console.info(`type: ${callback.type}, id: ${callback.id}, bufferSize: ${callback.bufferSize}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onGetReport(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## onInterruptDataReceived

```TypeScript
onInterruptDataReceived(callback: Callback<InterruptData>): void
```

订阅HID主机通过中断传输通道发送数据的事件的回调，使用callback异步回调。收到中断数据后，应用可根据报告ID解析并处理相应数据，例如处理主机下发的输出报告（如键盘LED状态指示等）。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterruptData](arkts-connectivity-hid-interruptdata-i.md)&gt; | 是 | 回调函数，返回收到的中断数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.InterruptData) {
    console.info(`id: ${callback.id}, dataSize: ${callback.data.length}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onInterruptDataReceived(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## onSetProtocol

```TypeScript
onSetProtocol(callback: Callback<ProtocolData>): void
```

订阅HID主机向HID设备发送的SET_PROTOCOL请求事件，使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProtocolData](arkts-connectivity-hid-protocoldata-i.md)&gt; | 是 | 回调函数。返回收到的协议数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.ProtocolData) {
    console.info(`protocol: ${callback.protocol}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onSetProtocol(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## onSetReport

```TypeScript
onSetReport(callback: Callback<SetReportData>): void
```

订阅HID主机向HID设备发送的SET_REPORT传输请求事件，使用callback异步回调。当收到的数据不符合预期时，可以通过调用接口[reportError](#reporterror)进行回复。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SetReportData](arkts-connectivity-hid-setreportdata-i.md)&gt; | 是 | 回调函数，返回收到的报告数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent(callback: hid.SetReportData) {
    console.info(`type: ${callback.type}, id: ${callback.id}, dataSize: ${callback.data.length}`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onSetReport(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## onVirtualCableUnplug

```TypeScript
onVirtualCableUnplug(callback: Callback<void>): void
```

订阅主机断开HID虚拟链路事件的回调。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。当主机断开虚拟链路时返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
function onReceiveEvent() {
    console.info(`onVirtualCableUnplug`);
}
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.onVirtualCableUnplug(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## registerHidDevice

```TypeScript
registerHidDevice(sdp: HidDeviceSdp, inQos: HidDeviceQos, outQos: HidDeviceQos, callback: Callback<boolean>): void
```

应用注册HID设备能力，以便与HID主机（如电脑、手机）进行通信。使用callback异步回调。

当应用调用该接口并注册成功后，可以通过调用[connect](#connect)接口连接HID主机。同一时间仅允许一个应用成功注册HID设备能力，同一应用重复注册将失败，注册成功后其他应用注册也将失败。当应用不再需要HID设备能力时，需要主动调用[unregisterHidDevice](#unregisterhiddevice)接口解除注册HID设备能力。调用该接口时，应用必须处于前台，否则无法注册成功。应用注册成功之后，若切换到后台，HID设备会自动解除注册，注册状态变化将通过回调上报给上层应用。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sdp | [HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md) | 是 | HID设备的服务能力记录，定义了设备类型、描述符等具体信息。 |
| inQos | [HidDeviceQos](arkts-connectivity-hid-hiddeviceqos-i.md) | 是 | 输入通道的Qos配置，用于定义对端到本端的数据流参数。 |
| outQos | [HidDeviceQos](arkts-connectivity-hid-hiddeviceqos-i.md) | 是 | 输出通道的Qos配置，用于定义本端到对端的数据流参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示HID设备当前为注册状态；返回false表示HID设备当前为解注册状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903050](../errorcode-bluetoothManager.md#2903050-hid不在前台) | Application is not in the foreground. |
| [2903051](../errorcode-bluetoothManager.md#2903051-hid已注册) | Any app has been registered. |

**示例**

```TypeScript
let descriptors: Uint8Array = new Uint8Array([
    // 描述符示例，需要遵循USB HID规范
    0x05, 0x01,        // 指定设备类别为通用桌面控制
    0x09, 0x06,        // 具体设备为键盘
    0xA1, 0x01,        // 应用集合开始

    // 按键字段定义
    0x05, 0x07,        // 切换到键盘/键区
    0x19, 0x00,        // 定义最小按键码为0（无按键）
    0x29, 0x01,        // 定义最大按键码为1（只支持2个值）
    0x15, 0x00,        // 逻辑最小值0（数据范围下限）
    0x25, 0x01,        // 逻辑最大值1（数据范围上限）
    0x75, 0x08,        // 每个字段八位
    0x95, 0x01,        // 只有一个字段
    0x81, 0x00,        // 定义输入字段：数据字段，值为按键数组

    // 结束设备定义
    0xC0               // 应用集合结束
]);
// 以键盘为例
let sdp: hid.HidDeviceSdp = {
    "name": "testName",
    "description": "testDescription",
    "provider": "testProvider",
    "subclass": hid.Subclass.SUBCLASS_KEYBOARD,
    "descriptors": descriptors,
};
let inqos: hid.HidDeviceQos = {
    "serviceType": hid.ServiceType.SERVICE_BEST_EFFORT,
    "tokenRate": 0,
    "tokenBucketSize": 0,
    "peakBandwidth": 0,
    "latency": -1,
    "delayVariation": -1,
};
let outqos: hid.HidDeviceQos = {};
function registerStateCallback(callback: boolean) {
    console.info(`state: ${callback}`);
}

try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.registerHidDevice(sdp, inqos, outqos, registerStateCallback)
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## replyReport

```TypeScript
replyReport(type: ReportType, id: number, reportData: Uint8Array): void
```

回复已连接HID主机的特定请求。

调用该接口前必须已调用[registerHidDevice](#registerhiddevice)完成注册，并通过[connect](#connect)建立与HID主机的连接。通过订阅[onGetReport](#ongetreport)应用可以接收主机的请求。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ReportType](arkts-connectivity-hid-reporttype-e.md) | 是 | 回复的报告类型，应与[onGetReport](#ongetreport)回调中收到的type保持一致。 |
| id | number | 是 | 对应HID设备注册时通过[HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。 |
| reportData | Uint8Array | 是 | 报告数据。其内容长度和解析方式必须严格匹配描述符中为该报告ID定义的格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903052](../errorcode-bluetoothManager.md#2903052-hid未注册) | App not register. |
| [2903053](../errorcode-bluetoothManager.md#2903053-hid未连接) | Device not connected. |

**示例**

```TypeScript
let type = hid.ReportType.REPORT_TYPE_INPUT;
let id: number = 0;
let reportData: Uint8Array = new Uint8Array([0x00, 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77]);
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.replyReport(type, id, reportData);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## reportError

```TypeScript
reportError(error: ErrorReason): void
```

向已连接的HID主机报告特定的错误类型。常用于在收到[onGetReport](#ongetreport)或[onSetReport](#onsetreport)回调后，当数据不符合预期时进行错误回复。

调用该接口前必须已调用[registerHidDevice](#registerhiddevice)完成注册，并通过[connect](#connect)建立与HID主机的连接。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [ErrorReason](arkts-connectivity-hid-errorreason-e.md) | 是 | 表示要报告给HID主机的具体错误类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903052](../errorcode-bluetoothManager.md#2903052-hid未注册) | App not register. |
| [2903053](../errorcode-bluetoothManager.md#2903053-hid未连接) | Device not connected. |

**示例**

```TypeScript
let error = hid.ErrorReason.RSP_SUCCESS;
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.reportError(error);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## sendReport

```TypeScript
sendReport(id: number, reportData: Uint8Array): void
```

向已连接的HID主机发送报告数据。

调用该接口前必须已调用[registerHidDevice](#registerhiddevice)完成注册，并通过[connect](#connect)建立与HID主机的连接。报告数据的长度和内容必须与HID设备注册时通过[HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md)所定义的规范保持一致，否则HID主机将无法正确解析。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 对应HID设备注册时通过[HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md)提供的描述符中定义的报告ID，用于标识报告类型，对于不带ID的简单设备，此参数应设置为0。对于定义了多个报告ID的设备，此处应传入对应的ID值，该ID值必须与描述符中定义的值保持一致。 |
| reportData | Uint8Array | 是 | 报告数据。其内容长度和解析方式必须严格匹配描述符中为该报告ID定义的格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2903052](../errorcode-bluetoothManager.md#2903052-hid未注册) | App not register. |
| [2903053](../errorcode-bluetoothManager.md#2903053-hid未连接) | Device not connected. |

**示例**

```TypeScript
let reportData: Uint8Array = new Uint8Array([0x00, 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77]);
let id: number = 0;
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.sendReport(id, reportData);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## unregisterHidDevice

```TypeScript
unregisterHidDevice(): void
```

解除注册本端作为HID设备的能力，并释放所有相关资源。

若调用该接口前，本端已通过调用[connect](#connect)建立与HID主机的连接，调用后本端与HID主机的连接会被断开。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    let hidDevice: hid.HidDeviceProfile = hid.createHidDeviceProfile();
    hidDevice.unregisterHidDevice();
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
