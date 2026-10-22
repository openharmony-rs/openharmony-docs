# bluetoothManager（蓝牙）

```TypeScript
declare namespace bluetoothManager
```

蓝牙模块提供了基础的传统蓝牙能力以及BLE的扫描、广播等功能。

从API Version 10 开始，该接口不再维护，推荐使用[@ohos.bluetooth.ble (蓝牙ble模块)](arkts-connectivity-bluetooth-ble.md)等相关Profile接口。

**起始版本：** 9

**废弃版本：** 10

<!--Device-unnamed-declare namespace bluetoothManager--><!--Device-unnamed-declare namespace bluetoothManager-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [BLE](arkts-connectivity-bluetoothmanager-ble-n.md) | BLE模块提供了对蓝牙操作和管理的方法。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [disableBluetooth](arkts-connectivity-bluetoothmanager-disablebluetooth-f.md#disablebluetooth-1) | 关闭蓝牙。 |
| [enableBluetooth](arkts-connectivity-bluetoothmanager-enablebluetooth-f.md#enablebluetooth-1) | 开启蓝牙。 |
| [getBluetoothScanMode](arkts-connectivity-bluetoothmanager-getbluetoothscanmode-f.md#getbluetoothscanmode-1) | 获取蓝牙扫描模式。 |
| [getBtConnectionState](arkts-connectivity-bluetoothmanager-getbtconnectionstate-f.md#getbtconnectionstate-1) | 获取蓝牙本端的Profile连接状态，例如：任意一个支持的Profile连接状态为已连接，则此接口返回状态为已连接。 |
| [getLocalName](arkts-connectivity-bluetoothmanager-getlocalname-f.md#getlocalname-1) | 获取蓝牙本地设备名称。 |
| [getPairedDevices](arkts-connectivity-bluetoothmanager-getpaireddevices-f.md#getpaireddevices-1) | 获取蓝牙配对列表。 |
| [getProfileConnectionState](arkts-connectivity-bluetoothmanager-getprofileconnectionstate-f.md#getprofileconnectionstate-1) | 依据ProfileId获取指定profile的连接状态。 |
| [getProfileInstance](arkts-connectivity-bluetoothmanager-getprofileinstance-f.md#getprofileinstance-1) | 通过ProfileId，获取profile的对象实例，API9新增了HidHostProfile，PanProfile。 |
| [getRemoteDeviceClass](arkts-connectivity-bluetoothmanager-getremotedeviceclass-f.md#getremotedeviceclass-1) | 获取对端蓝牙设备的类别。 |
| [getRemoteDeviceName](arkts-connectivity-bluetoothmanager-getremotedevicename-f.md#getremotedevicename-1) | 获取对端蓝牙设备的名称。 |
| [getState](arkts-connectivity-bluetoothmanager-getstate-f.md#getstate-1) | 获取蓝牙开关状态。 |
| [off('bluetoothDeviceFind')](arkts-connectivity-bluetoothmanager-off-f.md#offbluetoothdevicefind) | 取消订阅蓝牙设备发现上报事件。 |
| [off('bondStateChange')](arkts-connectivity-bluetoothmanager-off-f.md#offbondstatechange) | 取消订阅蓝牙配对状态改变事件。 |
| [off('pinRequired')](arkts-connectivity-bluetoothmanager-off-f.md#offpinrequired) | 取消订阅远端蓝牙设备的配对请求事件。 |
| [off('stateChange')](arkts-connectivity-bluetoothmanager-off-f.md#offstatechange) | 取消订阅蓝牙设备开关状态事件。 |
| [off('sppRead')](arkts-connectivity-bluetoothmanager-off-f.md#offsppread) | 取消订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [on('bluetoothDeviceFind')](arkts-connectivity-bluetoothmanager-on-f.md#onbluetoothdevicefind) | 订阅蓝牙设备发现上报事件。 |
| [on('bondStateChange')](arkts-connectivity-bluetoothmanager-on-f.md#onbondstatechange) | 订阅蓝牙配对状态改变事件。 |
| [on('pinRequired')](arkts-connectivity-bluetoothmanager-on-f.md#onpinrequired) | 订阅远端蓝牙设备的配对请求事件。 |
| [on('stateChange')](arkts-connectivity-bluetoothmanager-on-f.md#onstatechange) | 订阅蓝牙设备开关状态事件。 |
| [on('sppRead')](arkts-connectivity-bluetoothmanager-on-f.md#onsppread) | 订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [pairDevice](arkts-connectivity-bluetoothmanager-pairdevice-f.md#pairdevice-1) | 发起蓝牙配对。 |
| [setBluetoothScanMode](arkts-connectivity-bluetoothmanager-setbluetoothscanmode-f.md#setbluetoothscanmode-1) | 设置蓝牙扫描模式，可以被远端设备发现。 |
| [setDevicePairingConfirmation](arkts-connectivity-bluetoothmanager-setdevicepairingconfirmation-f.md#setdevicepairingconfirmation-1) | 设置设备配对请求确认。 |
| [setLocalName](arkts-connectivity-bluetoothmanager-setlocalname-f.md#setlocalname-1) | 设置蓝牙本地设备名称。 |
| [sppAccept](arkts-connectivity-bluetoothmanager-sppaccept-f.md#sppaccept-1) | 服务端监听socket等待客户端连接。 |
| [sppCloseClientSocket](arkts-connectivity-bluetoothmanager-sppcloseclientsocket-f.md#sppcloseclientsocket-1) | 关闭客户端socket，入参socket由sppAccept或sppConnect接口获取。 |
| [sppCloseServerSocket](arkts-connectivity-bluetoothmanager-sppcloseserversocket-f.md#sppcloseserversocket-1) | 关闭服务端监听Socket，入参socket由sppListen接口返回。 |
| [sppConnect](arkts-connectivity-bluetoothmanager-sppconnect-f.md#sppconnect-1) | 客户端向远端设备发起spp连接。 |
| [sppListen](arkts-connectivity-bluetoothmanager-spplisten-f.md#spplisten-1) | 创建一个服务端监听Socket。 |
| [sppWrite](arkts-connectivity-bluetoothmanager-sppwrite-f.md#sppwrite-1) | 通过socket向远端发送数据，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [startBluetoothDiscovery](arkts-connectivity-bluetoothmanager-startbluetoothdiscovery-f.md#startbluetoothdiscovery-1) | 开启蓝牙扫描，可以发现远端设备。 |
| [stopBluetoothDiscovery](arkts-connectivity-bluetoothmanager-stopbluetoothdiscovery-f.md#stopbluetoothdiscovery-1) | 关闭蓝牙扫描。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetoothmanager-cancelpaireddevice-f-sys.md#cancelpaireddevice-1) | 删除配对的远程设备。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [A2dpSourceProfile](arkts-connectivity-bluetoothmanager-a2dpsourceprofile-i.md) | 使用A2dpSourceProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [AdvertiseData](arkts-connectivity-bluetoothmanager-advertisedata-i.md) | 描述BLE广播数据包的内容。 |
| [AdvertiseSetting](arkts-connectivity-bluetoothmanager-advertisesetting-i.md) | 描述蓝牙低功耗设备发送广播的参数。 |
| [BaseProfile](arkts-connectivity-bluetoothmanager-baseprofile-i.md) | profile基类。 |
| [BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md) | 描述characteristic的接口参数定义。 |
| [BLEConnectChangedState](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md) | 描述Gatt profile连接状态。 |
| [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md) | 描述descriptor的接口参数定义。 |
| [BondStateParam](arkts-connectivity-bluetoothmanager-bondstateparam-i.md) | 描述配对状态参数。 |
| [CharacteristicReadRequest](arkts-connectivity-bluetoothmanager-characteristicreadrequest-i.md) | 描述server端订阅后收到的特征值读请求事件参数结构。 |
| [CharacteristicWriteRequest](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md) | 描述server端订阅后收到的特征值写请求事件参数结构。 |
| [DescriptorReadRequest](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md) | 描述server端订阅后收到的描述符读请求事件参数结构。 |
| [DescriptorWriteRequest](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md) | 描述server端订阅后收到的描述符写请求事件参数结构。 |
| [DeviceClass](arkts-connectivity-bluetoothmanager-deviceclass-i.md) | 描述蓝牙设备的类别。 |
| [GattClientDevice](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md) | client端类，使用client端方法之前需要创建该类的实例进行操作，通过createGattClientDevice(deviceId: string)方法构造此实例。 |
| [GattServer](arkts-connectivity-bluetoothmanager-gattserver-i.md) | server端类，使用server端方法之前需要创建该类的实例进行操作，通过createGattServer()方法构造此实例。 |
| [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) | 描述service的接口参数定义。 |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetoothmanager-handsfreeaudiogatewayprofile-i.md) | 使用HandsFreeAudioGatewayProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) | 使用HidHostProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [ManufactureData](arkts-connectivity-bluetoothmanager-manufacturedata-i.md) | 描述BLE广播数据包的内容。 |
| [NotifyCharacteristic](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md) | 描述server端特征值变化时发送的特征通知参数定义。 |
| [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i.md) | 使用PanProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [PinRequiredParam](arkts-connectivity-bluetoothmanager-pinrequiredparam-i.md) | 描述配对请求参数。 |
| [ScanFilter](arkts-connectivity-bluetoothmanager-scanfilter-i.md) | 扫描过滤参数。 |
| [ScanOptions](arkts-connectivity-bluetoothmanager-scanoptions-i.md) | 扫描的配置参数。 |
| [ScanResult](arkts-connectivity-bluetoothmanager-scanresult-i.md) | 扫描结果上报数据。 |
| [ServerResponse](arkts-connectivity-bluetoothmanager-serverresponse-i.md) | 描述server端回复client端读/写请求的响应参数结构。 |
| [ServiceData](arkts-connectivity-bluetoothmanager-servicedata-i.md) | 描述广播包中服务数据内容。 |
| [SppOption](arkts-connectivity-bluetoothmanager-sppoption-i.md) | 描述spp的配置参数。 |
| [StateChangeParam](arkts-connectivity-bluetoothmanager-statechangeparam-i.md) | 描述profile状态改变参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i-sys.md) | 使用HidHostProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i-sys.md) | 使用PanProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BluetoothState](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md) | 枚举，蓝牙开关状态。 |
| [BondState](arkts-connectivity-bluetoothmanager-bondstate-e.md) | 枚举，配对状态。 |
| [MajorClass](arkts-connectivity-bluetoothmanager-majorclass-e.md) | 枚举，蓝牙设备主要类别。 |
| [MajorMinorClass](arkts-connectivity-bluetoothmanager-majorminorclass-e.md) | 枚举，主要次要蓝牙设备类别。 |
| [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md) | 枚举，硬件过滤匹配模式。 |
| [PlayingState](arkts-connectivity-bluetoothmanager-playingstate-e.md) | 枚举，蓝牙A2DP 播放状态。 |
| [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md) | 枚举，蓝牙设备的profile连接状态。 |
| [ProfileId](arkts-connectivity-bluetoothmanager-profileid-e.md) | 蓝牙profile枚举，API9新增PROFILE_HID_HOST，PROFILE_PAN_NETWORK。 |
| [ScanDuty](arkts-connectivity-bluetoothmanager-scanduty-e.md) | 枚举，扫描模式。 |
| [ScanMode](arkts-connectivity-bluetoothmanager-scanmode-e.md) | 枚举，扫描模式。 |
| [SppType](arkts-connectivity-bluetoothmanager-spptype-e.md) | 枚举，Spp链路类型。 |
