# on

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## on('bluetoothDeviceFind')

```TypeScript
function on(type: 'bluetoothDeviceFind', callback: Callback<Array<string>>): void
```

订阅蓝牙设备发现上报事件。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** bluetoothDeviceFind

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bluetoothDeviceFind' | 是 | 填写"bluetoothDeviceFind"字符串，表示蓝牙设备发现事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 表示回调函数的入参，发现的设备集合。回调函数由用户创建通过该接口注册。 |


## on('bondStateChange')

```TypeScript
function on(type: 'bondStateChange', callback: Callback<BondStateParam>): void
```

订阅蓝牙配对状态改变事件。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** bondStateChange

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'bondStateChange' | 是 | 填写"bondStateChange"字符串，表示蓝牙配对状态改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BondStateParam](arkts-connectivity-bluetooth-bondstateparam-i.md)&gt; | 是 | 表示回调函数的入参，配对的状态。回调函数由用户创建通过该接口注册。 |


## on('pinRequired')

```TypeScript
function on(type: 'pinRequired', callback: Callback<PinRequiredParam>): void
```

订阅远端蓝牙设备的配对请求事件。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** pinRequired

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'pinRequired' | 是 | 填写"pinRequired"字符串，表示配对请求事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PinRequiredParam](arkts-connectivity-bluetooth-pinrequiredparam-i.md)&gt; | 是 | 表示回调函数的入参，配对请求。回调函数由用户创建通过该接口注册。 |


## on('stateChange')

```TypeScript
function on(type: 'stateChange', callback: Callback<BluetoothState>): void
```

订阅蓝牙连接状态改变事件。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stateChange

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 填写"stateChange"字符串，表示蓝牙状态改变事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md)&gt; | 是 | 表示回调函数的入参，蓝牙状态。回调函数由用户创建通过该接口注册。 |


## on('sppRead')

```TypeScript
function on(type: 'sppRead', clientSocket: number, callback: Callback<ArrayBuffer>): void
```

从API version 8开始支持，从API version 9开始废弃。订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sppRead

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sppRead' | 是 | 填写"sppRead"字符串，表示spp读请求事件。 |
| clientSocket | number | 是 | 客户端socket的id。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | 是 | 表示回调函数的入参，读取到的数据。 |
