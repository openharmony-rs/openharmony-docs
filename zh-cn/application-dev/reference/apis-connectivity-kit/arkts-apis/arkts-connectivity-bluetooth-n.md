# bluetooth（蓝牙）

```TypeScript
declare namespace bluetooth
```

蓝牙模块提供了基础的传统蓝牙能力以及BLE的扫描、广播等功能。

从API Version 9 开始，该接口不再维护，推荐使用[@ohos.bluetooth.ble (蓝牙ble模块)](arkts-connectivity-bluetooth-ble.md)等相关Profile接口。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bluetoothManager

<!--Device-unnamed-declare namespace bluetooth--><!--Device-unnamed-declare namespace bluetooth-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [BLE](arkts-connectivity-bluetooth-ble-n.md) |  |

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableBluetooth](arkts-connectivity-bluetooth-disablebluetooth-f.md#disablebluetooth) | 关闭蓝牙。 |
| [enableBluetooth](arkts-connectivity-bluetooth-enablebluetooth-f.md#enablebluetooth) | 开启蓝牙。 |
| [getBluetoothScanMode](arkts-connectivity-bluetooth-getbluetoothscanmode-f.md#getbluetoothscanmode) | 获取蓝牙扫描模式。 |
| [getBtConnectionState](arkts-connectivity-bluetooth-getbtconnectionstate-f.md#getbtconnectionstate) | 获取蓝牙本端的Profile连接状态，例如：任意一个支持的Profile连接状态为已连接，则此接口返回状态为已连接。 |
| [getLocalName](arkts-connectivity-bluetooth-getlocalname-f.md#getlocalname) | 获取蓝牙本地设备名称。 |
| [getPairedDevices](arkts-connectivity-bluetooth-getpaireddevices-f.md#getpaireddevices) | 获取蓝牙配对列表。 |
| [getProfile](arkts-connectivity-bluetooth-getprofile-f.md#getprofile) | 通过ProfileId，获取profile的对象实例。 |
| [getProfileConnState](arkts-connectivity-bluetooth-getprofileconnstate-f.md#getprofileconnstate) | 依据ProfileId获取指定profile的连接状态。 |
| [getRemoteDeviceClass](arkts-connectivity-bluetooth-getremotedeviceclass-f.md#getremotedeviceclass) | 获取对端蓝牙设备的类别。 |
| [getRemoteDeviceName](arkts-connectivity-bluetooth-getremotedevicename-f.md#getremotedevicename) | 获取对端蓝牙设备的名称。 |
| [getState](arkts-connectivity-bluetooth-getstate-f.md#getstate) | 获取蓝牙开关状态。 |
| [off('bluetoothDeviceFind')](arkts-connectivity-bluetooth-off-f.md#offbluetoothdevicefind) | 取消订阅蓝牙设备发现上报事件。 |
| [off('bondStateChange')](arkts-connectivity-bluetooth-off-f.md#offbondstatechange) | 取消订阅蓝牙配对状态改变事件。 |
| [off('pinRequired')](arkts-connectivity-bluetooth-off-f.md#offpinrequired) | 取消订阅远端蓝牙设备的配对请求事件。 |
| [off('stateChange')](arkts-connectivity-bluetooth-off-f.md#offstatechange) | 取消订阅蓝牙连接状态改变事件。 |
| [off('sppRead')](arkts-connectivity-bluetooth-off-f.md#offsppread) | 取消订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [on('bluetoothDeviceFind')](arkts-connectivity-bluetooth-on-f.md#onbluetoothdevicefind) | 订阅蓝牙设备发现上报事件。 |
| [on('bondStateChange')](arkts-connectivity-bluetooth-on-f.md#onbondstatechange) | 订阅蓝牙配对状态改变事件。 |
| [on('pinRequired')](arkts-connectivity-bluetooth-on-f.md#onpinrequired) | 订阅远端蓝牙设备的配对请求事件。 |
| [on('stateChange')](arkts-connectivity-bluetooth-on-f.md#onstatechange) | 订阅蓝牙连接状态改变事件。 |
| [on('sppRead')](arkts-connectivity-bluetooth-on-f.md#onsppread) | 从API version 8开始支持，从API version 9开始废弃。订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [pairDevice](arkts-connectivity-bluetooth-pairdevice-f.md#pairdevice) | 发起蓝牙配对。 |
| [setBluetoothScanMode](arkts-connectivity-bluetooth-setbluetoothscanmode-f.md#setbluetoothscanmode) | 设置蓝牙扫描模式，可以被远端设备发现。 |
| [setDevicePairingConfirmation](arkts-connectivity-bluetooth-setdevicepairingconfirmation-f.md#setdevicepairingconfirmation) | 设置设备配对请求确认。 |
| [setLocalName](arkts-connectivity-bluetooth-setlocalname-f.md#setlocalname) | 设置蓝牙本地设备名称。 |
| [sppAccept](arkts-connectivity-bluetooth-sppaccept-f.md#sppaccept) | 服务端监听socket等待客户端连接。 |
| [sppCloseClientSocket](arkts-connectivity-bluetooth-sppcloseclientsocket-f.md#sppcloseclientsocket) | 关闭客户端socket，入参socket由sppAccept或sppConnect接口获取。 |
| [sppCloseServerSocket](arkts-connectivity-bluetooth-sppcloseserversocket-f.md#sppcloseserversocket) | 关闭服务端监听Socket，入参socket由sppListen接口返回。 |
| [sppConnect](arkts-connectivity-bluetooth-sppconnect-f.md#sppconnect) | 客户端向远端设备发起spp连接。 |
| [sppListen](arkts-connectivity-bluetooth-spplisten-f.md#spplisten) | 创建一个服务端监听Socket。 |
| [sppWrite](arkts-connectivity-bluetooth-sppwrite-f.md#sppwrite) | 通过socket向远端发送数据，入参clientSocket由sppAccept或sppConnect接口获取 。 |
| [startBluetoothDiscovery](arkts-connectivity-bluetooth-startbluetoothdiscovery-f.md#startbluetoothdiscovery) | 开启蓝牙扫描，可以发现远端设备。 |
| [stopBluetoothDiscovery](arkts-connectivity-bluetooth-stopbluetoothdiscovery-f.md#stopbluetoothdiscovery) | 关闭蓝牙扫描。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetooth-cancelpaireddevice-f-sys.md#cancelpaireddevice) | 删除配对的远程设备。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetooth-a2dpsourceprofile-i.md) | 使用A2dpSourceProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [AdvertiseData](arkts-connectivity-bluetooth-advertisedata-i.md) | 描述BLE广播数据包的内容。 |
| [AdvertiseSetting](arkts-connectivity-bluetooth-advertisesetting-i.md) | 描述蓝牙低功耗设备发送广播的参数。 |
| [BaseProfile](arkts-connectivity-bluetooth-baseprofile-i.md) | profile基类。 |
| [BLECharacteristic](arkts-connectivity-bluetooth-blecharacteristic-i.md) | 描述characteristic的接口参数定义 。 |
| [BLEConnectChangedState](arkts-connectivity-bluetooth-bleconnectchangedstate-i.md) | 描述Gatt profile连接状态 。 |
| [BLEDescriptor](arkts-connectivity-bluetooth-bledescriptor-i.md) | 描述descriptor的接口参数定义 。 |
| [BondStateParam](arkts-connectivity-bluetooth-bondstateparam-i.md) | 描述配对状态参数。 |
| [CharacteristicReadReq](arkts-connectivity-bluetooth-characteristicreadreq-i.md) | 描述server端订阅后收到的特征值读请求事件参数结构。 |
| [CharacteristicWriteReq](arkts-connectivity-bluetooth-characteristicwritereq-i.md) | 描述server端订阅后收到的特征值写请求事件参数结构。 |
| [DescriptorReadReq](arkts-connectivity-bluetooth-descriptorreadreq-i.md) | 描述server端订阅后收到的描述符读请求事件参数结构。 |
| [DescriptorWriteReq](arkts-connectivity-bluetooth-descriptorwritereq-i.md) | 描述server端订阅后收到的描述符写请求事件参数结构。 |
| [DeviceClass](arkts-connectivity-bluetooth-deviceclass-i.md) | 描述蓝牙设备的类别。 |
| [GattClientDevice](arkts-connectivity-bluetooth-gattclientdevice-i.md) | client端类，使用client端方法之前需要创建该类的实例进行操作，通过createGattClientDevice(deviceId: string)方法构造此实例。 |
| [GattServer](arkts-connectivity-bluetooth-gattserver-i.md) | server端类，使用server端方法之前需要创建该类的实例进行操作，通过createGattServer()方法构造此实例。 |
| [GattService](arkts-connectivity-bluetooth-gattservice-i.md) | 描述service的接口参数定义。 |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetooth-handsfreeaudiogatewayprofile-i.md) | 使用HandsFreeAudioGatewayProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [ManufactureData](arkts-connectivity-bluetooth-manufacturedata-i.md) | 描述BLE广播数据包的内容。 |
| [NotifyCharacteristic](arkts-connectivity-bluetooth-notifycharacteristic-i.md) | 描述server端特征值变化时发送的特征通知参数定义。 |
| [PinRequiredParam](arkts-connectivity-bluetooth-pinrequiredparam-i.md) | 描述配对请求参数。 |
| [ScanFilter](arkts-connectivity-bluetooth-scanfilter-i.md) | 扫描过滤参数。 |
| [ScanOptions](arkts-connectivity-bluetooth-scanoptions-i.md) | 扫描的配置参数。 |
| [ScanResult](arkts-connectivity-bluetooth-scanresult-i.md) | 扫描结果上报数据。 |
| [ServerResponse](arkts-connectivity-bluetooth-serverresponse-i.md) | 描述server端回复client端读/写请求的响应参数结构。 |
| [ServiceData](arkts-connectivity-bluetooth-servicedata-i.md) | 描述广播包中服务数据内容。 |
| [SppOption](arkts-connectivity-bluetooth-sppoption-i.md) | 描述spp的配置参数。 |
| [StateChangeParam](arkts-connectivity-bluetooth-statechangeparam-i.md) | 描述profile状态改变参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetooth-bluetoothstate-e.md) | 枚举，蓝牙开关状态。 |
| [BondState](arkts-connectivity-bluetooth-bondstate-e.md) | 枚举，配对状态。 |
| [MajorClass](arkts-connectivity-bluetooth-majorclass-e.md) | 枚举，蓝牙设备主要类别。 |
| [MajorMinorClass](arkts-connectivity-bluetooth-majorminorclass-e.md) | 枚举，主要次要蓝牙设备类别。 |
| [MatchMode](arkts-connectivity-bluetooth-matchmode-e.md) | 枚举，硬件过滤匹配模式。 |
| [PlayingState](arkts-connectivity-bluetooth-playingstate-e.md) | 枚举，蓝牙A2DP 播放状态。 |
| [ProfileConnectionState](arkts-connectivity-bluetooth-profileconnectionstate-e.md) | 枚举，蓝牙设备的profile连接状态。 |
| [ProfileId](arkts-connectivity-bluetooth-profileid-e.md) | 蓝牙profile枚举，API9新增PROFILE_HID_HOST，PROFILE_PAN_NETWORK。 |
| [ScanDuty](arkts-connectivity-bluetooth-scanduty-e.md) | 枚举，扫描模式。 |
| [ScanMode](arkts-connectivity-bluetooth-scanmode-e.md) | 枚举，扫描模式。 |
| [SppType](arkts-connectivity-bluetooth-spptype-e.md) | 枚举，Spp链路类型。 |
