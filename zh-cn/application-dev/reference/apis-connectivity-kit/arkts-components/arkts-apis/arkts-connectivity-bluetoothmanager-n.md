# bluetoothManager(蓝牙)

```TypeScript
declare namespace bluetoothManager
```

蓝牙模块提供了基础的传统蓝牙能力以及BLE的扫描、广播等功能。

从API Version 10 开始，该接口不再维护，推荐使用[@ohos.bluetooth.ble (蓝牙ble模块)](arkts-connectivity-bluetooth-ble.md)等相关Profile接口。

**起始版本：** 9

**废弃版本：** 10

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
| [getState](arkts-connectivity-bluetoothmanager-getstate-f.md) | 获取蓝牙开关状态。 |
| [getBtConnectionState](arkts-connectivity-bluetoothmanager-getbtconnectionstate-f.md) | 获取蓝牙本端的Profile连接状态，例如：任意一个支持的Profile连接状态为已连接，则此接口返回状态为已连接。 |
| [pairDevice](arkts-connectivity-bluetoothmanager-pairdevice-f.md) | 发起蓝牙配对。 |
| [getRemoteDeviceName](arkts-connectivity-bluetoothmanager-getremotedevicename-f.md) | 获取对端蓝牙设备的名称。 |
| [getRemoteDeviceClass](arkts-connectivity-bluetoothmanager-getremotedeviceclass-f.md) | 获取对端蓝牙设备的类别。 |
| [enableBluetooth](arkts-connectivity-bluetoothmanager-enablebluetooth-f.md) | 开启蓝牙。 |
| [disableBluetooth](arkts-connectivity-bluetoothmanager-disablebluetooth-f.md) | 关闭蓝牙。 |
| [getLocalName](arkts-connectivity-bluetoothmanager-getlocalname-f.md) | 获取蓝牙本地设备名称。 |
| [getPairedDevices](arkts-connectivity-bluetoothmanager-getpaireddevices-f.md) | 获取蓝牙配对列表。 |
| [getProfileConnectionState](arkts-connectivity-bluetoothmanager-getprofileconnectionstate-f.md) | 依据ProfileId获取指定profile的连接状态。 |
| [setDevicePairingConfirmation](arkts-connectivity-bluetoothmanager-setdevicepairingconfirmation-f.md) | 设置设备配对请求确认。 |
| [setLocalName](arkts-connectivity-bluetoothmanager-setlocalname-f.md) | 设置蓝牙本地设备名称。 |
| [setBluetoothScanMode](arkts-connectivity-bluetoothmanager-setbluetoothscanmode-f.md) | 设置蓝牙扫描模式，可以被远端设备发现。 |
| [getBluetoothScanMode](arkts-connectivity-bluetoothmanager-getbluetoothscanmode-f.md) | 获取蓝牙扫描模式。 |
| [startBluetoothDiscovery](arkts-connectivity-bluetoothmanager-startbluetoothdiscovery-f.md) | 开启蓝牙扫描，可以发现远端设备。 |
| [stopBluetoothDiscovery](arkts-connectivity-bluetoothmanager-stopbluetoothdiscovery-f.md) | 关闭蓝牙扫描。 |
| [on](arkts-connectivity-bluetoothmanager-on-f.md#onbluetoothdevicefind) | 订阅蓝牙设备发现上报事件。 |
| [off](arkts-connectivity-bluetoothmanager-off-f.md#offbluetoothdevicefind) | 取消订阅蓝牙设备发现上报事件。 |
| [on](arkts-connectivity-bluetoothmanager-on-f.md#onbondstatechange) | 订阅蓝牙配对状态改变事件。 |
| [off](arkts-connectivity-bluetoothmanager-off-f.md#offbondstatechange) | 取消订阅蓝牙配对状态改变事件。 |
| [on](arkts-connectivity-bluetoothmanager-on-f.md#onpinrequired) | 订阅远端蓝牙设备的配对请求事件。 |
| [off](arkts-connectivity-bluetoothmanager-off-f.md#offpinrequired) | 取消订阅远端蓝牙设备的配对请求事件。 |
| [on](arkts-connectivity-bluetoothmanager-on-f.md#onstatechange) | 订阅蓝牙设备开关状态事件。 |
| [off](arkts-connectivity-bluetoothmanager-off-f.md#offstatechange) | 取消订阅蓝牙设备开关状态事件。 |
| [sppListen](arkts-connectivity-bluetoothmanager-spplisten-f.md) | 创建一个服务端监听Socket。 |
| [sppAccept](arkts-connectivity-bluetoothmanager-sppaccept-f.md) | 服务端监听socket等待客户端连接。 |
| [sppConnect](arkts-connectivity-bluetoothmanager-sppconnect-f.md) | 客户端向远端设备发起spp连接。 |
| [sppCloseServerSocket](arkts-connectivity-bluetoothmanager-sppcloseserversocket-f.md) | 关闭服务端监听Socket，入参socket由sppListen接口返回。 |
| [sppCloseClientSocket](arkts-connectivity-bluetoothmanager-sppcloseclientsocket-f.md) | 关闭客户端socket，入参socket由sppAccept或sppConnect接口获取。 |
| [sppWrite](arkts-connectivity-bluetoothmanager-sppwrite-f.md) | 通过socket向远端发送数据，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [on](arkts-connectivity-bluetoothmanager-on-f.md#onsppread) | 订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [off](arkts-connectivity-bluetoothmanager-off-f.md#offsppread) | 取消订阅spp读请求事件，入参clientSocket由sppAccept或sppConnect接口获取。 |
| [getProfileInstance](arkts-connectivity-bluetoothmanager-getprofileinstance-f.md) | 通过ProfileId，获取profile的对象实例，API9新增了HidHostProfile，PanProfile。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-bluetoothmanager-cancelpaireddevice-f-sys.md) | 删除配对的远程设备。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-bluetoothmanager-baseprofile-i.md) | profile基类。 |
| [A2dpSourceProfile](arkts-connectivity-bluetoothmanager-a2dpsourceprofile-i.md) | 使用A2dpSourceProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [HandsFreeAudioGatewayProfile](arkts-connectivity-bluetoothmanager-handsfreeaudiogatewayprofile-i.md) | 使用HandsFreeAudioGatewayProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) | 使用HidHostProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [PanProfile](arkts-connectivity-bluetoothmanager-panprofile-i.md) | 使用PanProfile方法之前需要创建该类的实例进行操作，通过getProfile()方法构造此实例。 |
| [GattServer](arkts-connectivity-bluetoothmanager-gattserver-i.md) | server端类，使用server端方法之前需要创建该类的实例进行操作，通过createGattServer()方法构造此实例。 |
| [GattClientDevice](arkts-connectivity-bluetoothmanager-gattclientdevice-i.md) | client端类，使用client端方法之前需要创建该类的实例进行操作，通过createGattClientDevice(deviceId: string)方法构造此实例。 |
| [GattService](arkts-connectivity-bluetoothmanager-gattservice-i.md) | 描述service的接口参数定义。 |
| [BLECharacteristic](arkts-connectivity-bluetoothmanager-blecharacteristic-i.md) | 描述characteristic的接口参数定义。 |
| [BLEDescriptor](arkts-connectivity-bluetoothmanager-bledescriptor-i.md) | 描述descriptor的接口参数定义。 |
| [NotifyCharacteristic](arkts-connectivity-bluetoothmanager-notifycharacteristic-i.md) | 描述server端特征值变化时发送的特征通知参数定义。 |
| [CharacteristicReadRequest](arkts-connectivity-bluetoothmanager-characteristicreadrequest-i.md) | 描述server端订阅后收到的特征值读请求事件参数结构。 |
| [CharacteristicWriteRequest](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md) | 描述server端订阅后收到的特征值写请求事件参数结构。 |
| [DescriptorReadRequest](arkts-connectivity-bluetoothmanager-descriptorreadrequest-i.md) | 描述server端订阅后收到的描述符读请求事件参数结构。 |
| [DescriptorWriteRequest](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md) | 描述server端订阅后收到的描述符写请求事件参数结构。 |
| [ServerResponse](arkts-connectivity-bluetoothmanager-serverresponse-i.md) | 描述server端回复client端读/写请求的响应参数结构。 |
| [BLEConnectChangedState](arkts-connectivity-bluetoothmanager-bleconnectchangedstate-i.md) | 描述Gatt profile连接状态。 |
| [ScanResult](arkts-connectivity-bluetoothmanager-scanresult-i.md) | 扫描结果上报数据。 |
| [AdvertiseSetting](arkts-connectivity-bluetoothmanager-advertisesetting-i.md) | 描述蓝牙低功耗设备发送广播的参数。 |
| [AdvertiseData](arkts-connectivity-bluetoothmanager-advertisedata-i.md) | 描述BLE广播数据包的内容。 |
| [ManufactureData](arkts-connectivity-bluetoothmanager-manufacturedata-i.md) | 描述BLE广播数据包的内容。 |
| [ServiceData](arkts-connectivity-bluetoothmanager-servicedata-i.md) | 描述广播包中服务数据内容。 |
| [ScanFilter](arkts-connectivity-bluetoothmanager-scanfilter-i.md) | 扫描过滤参数。 |
| [ScanOptions](arkts-connectivity-bluetoothmanager-scanoptions-i.md) | 扫描的配置参数。 |
| [SppOption](arkts-connectivity-bluetoothmanager-sppoption-i.md) | 描述spp的配置参数。 |
| [PinRequiredParam](arkts-connectivity-bluetoothmanager-pinrequiredparam-i.md) | 描述配对请求参数。 |
| [DeviceClass](arkts-connectivity-bluetoothmanager-deviceclass-i.md) | 描述蓝牙设备的类别。 |
| [BondStateParam](arkts-connectivity-bluetoothmanager-bondstateparam-i.md) | 描述配对状态参数。 |
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
| [ScanDuty](arkts-connectivity-bluetoothmanager-scanduty-e.md) | 枚举，扫描模式。 |
| [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md) | 枚举，硬件过滤匹配模式。 |
| [ProfileConnectionState](arkts-connectivity-bluetoothmanager-profileconnectionstate-e.md) | 枚举，蓝牙设备的profile连接状态。 |
| [BluetoothState](arkts-connectivity-bluetoothmanager-bluetoothstate-e.md) | 枚举，蓝牙开关状态。 |
| [SppType](arkts-connectivity-bluetoothmanager-spptype-e.md) | 枚举，Spp链路类型。 |
| [ScanMode](arkts-connectivity-bluetoothmanager-scanmode-e.md) | 枚举，扫描模式。 |
| [BondState](arkts-connectivity-bluetoothmanager-bondstate-e.md) | 枚举，配对状态。 |
| [MajorClass](arkts-connectivity-bluetoothmanager-majorclass-e.md) | 枚举，蓝牙设备主要类别。 |
| [MajorMinorClass](arkts-connectivity-bluetoothmanager-majorminorclass-e.md) | 枚举，主要次要蓝牙设备类别。 |
| [PlayingState](arkts-connectivity-bluetoothmanager-playingstate-e.md) | 枚举，蓝牙A2DP 播放状态。 |
| [ProfileId](arkts-connectivity-bluetoothmanager-profileid-e.md) | 蓝牙profile枚举，API9新增PROFILE_HID_HOST，PROFILE_PAN_NETWORK。 |
