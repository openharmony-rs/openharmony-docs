# @ohos.bluetooth.connection(蓝牙connection模块)

connection模块提供了蓝牙设备的配对、连接、状态查询、设备扫描发现、扫描模式设置、电量信息获取及事件订阅等能力，适用于需要在应用中实现蓝牙设备发现、配对、连接和信息查询的场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [connectAllowedProfiles](arkts-connectivity-connection-connectallowedprofiles-f.md) | 连接对端设备支持的Profile（只包括A2DP、HFP和HID）。使用Callback异步回调。 |
| [connectAllowedProfiles](arkts-connectivity-connection-connectallowedprofiles-f.md) | 连接对端设备支持的Profile（只包括A2DP、HFP和HID）。使用Promise异步回调。 |
| [disconnectAllowedProfiles](arkts-connectivity-connection-disconnectallowedprofiles-f.md) | 断开对端设备支持的Profile（只包括A2DP和HFP）。 |
| [getBluetoothScanMode](arkts-connectivity-connection-getbluetoothscanmode-f.md) | 获取蓝牙扫描模式。搭配[onScanModeChange](arkts-connectivity-connection-onscanmodechange-f.md)接口使用，可实时监听蓝牙扫描模式变更事件。 |
| [getLastConnectionTime](arkts-connectivity-connection-getlastconnectiontime-f.md) | 获取对端蓝牙设备最近一次连接的时间点。使用Promise异步回调。 |
| [getLocalName](arkts-connectivity-connection-getlocalname-f.md) | 获取本机蓝牙设备的名称。 |
| [getPairedDevices](arkts-connectivity-connection-getpaireddevices-f.md) | 获取已配对蓝牙设备的地址集合。 |
| [getPairState](arkts-connectivity-connection-getpairstate-f.md) | 获取对端蓝牙设备的配对状态信息。 |
| [getProfileConnectionState](arkts-connectivity-connection-getprofileconnectionstate-f.md) | 获取蓝牙Profile协议的连接状态，其中ProfileId为可选参数。 |
| [getRemoteDeviceBatteryInfo](arkts-connectivity-connection-getremotedevicebatteryinfo-f.md) | 获取对端蓝牙设备的电量信息。使用Promise异步回调。 |
| [getRemoteDeviceClass](arkts-connectivity-connection-getremotedeviceclass-f.md) | 获取对端蓝牙设备的类别。 |
| [getRemoteDeviceName](arkts-connectivity-connection-getremotedevicename-f.md) | 获取对端蓝牙设备的名称。 |
| [getRemoteDeviceName](arkts-connectivity-connection-getremotedevicename-f.md) | 获取对端蓝牙设备的名称，其中alias为可选参数。 |
| [getRemoteDeviceTransport](arkts-connectivity-connection-getremotedevicetransport-f.md) | 获取对端蓝牙设备的传输类型。 |
| [getRemoteProfileUuids](arkts-connectivity-connection-getremoteprofileuuids-f.md) | 获取对端蓝牙设备的Profile协议能力，通过UUID区分。使用Callback异步回调。 |
| [getRemoteProfileUuids](arkts-connectivity-connection-getremoteprofileuuids-f.md) | 获取对端蓝牙设备的Profile协议能力，通过UUID区分。使用Promise异步回调。 |
| [getVirtualAddressByHash](arkts-connectivity-connection-getvirtualaddressbyhash-f.md) | 根据已配对设备实际MAC地址的哈希值获取对应的虚拟MAC地址。 |
| [isBluetoothDiscovering](arkts-connectivity-connection-isbluetoothdiscovering-f.md) | 判断本机蓝牙设备是否处于设备扫描状态。 |
| [off](arkts-connectivity-connection-off-f.md#offbluetoothdevicefind) | 取消订阅蓝牙设备扫描结果上报事件。 |
| [off](arkts-connectivity-connection-off-f.md#offdiscoveryresult) | 取消订阅蓝牙设备扫描结果上报事件。 |
| [off](arkts-connectivity-connection-off-f.md#offbondstatechange) | 取消订阅蓝牙配对状态变化事件。 |
| [off](arkts-connectivity-connection-off-f.md#offpinrequired) | 取消订阅配对请求事件。 |
| [off](arkts-connectivity-connection-off-f.md#offbatterychange) | 取消订阅对端设备的电量信息变化事件。 |
| [offAclStateChange](arkts-connectivity-connection-offaclstatechange-f.md) | 取消订阅蓝牙ACL链路连接状态变化事件。 |
| [offScanModeChange](arkts-connectivity-connection-offscanmodechange-f.md) | 取消订阅蓝牙扫描模式变更事件。 |
| [on](arkts-connectivity-connection-on-f.md#onbluetoothdevicefind) | 订阅蓝牙设备扫描结果上报事件。使用Callback异步回调。 |
| [on](arkts-connectivity-connection-on-f.md#ondiscoveryresult) | 订阅蓝牙设备扫描结果上报事件。使用Callback异步回调。 |
| [on](arkts-connectivity-connection-on-f.md#onbondstatechange) | 订阅蓝牙配对状态变化事件。使用Callback异步回调。 |
| [on](arkts-connectivity-connection-on-f.md#onpinrequired) | 订阅配对请求事件。使用Callback异步回调。 |
| [on](arkts-connectivity-connection-on-f.md#onbatterychange) | 订阅对端设备的电量信息变化事件。使用Callback异步回调。 |
| [onAclStateChange](arkts-connectivity-connection-onaclstatechange-f.md) | 订阅蓝牙ACL链路连接状态变化事件。当触发蓝牙ACL链路连接或断开时，如订阅此事件，则会收到携带对应设备的地址与连接状态的回调函数。 |
| [onScanModeChange](arkts-connectivity-connection-onscanmodechange-f.md) | 订阅蓝牙扫描模式变更事件。使用Callback异步回调。当调用[setBluetoothScanMode](arkts-connectivity-connection-setbluetoothscanmode-f.md)更改当前蓝牙扫描模式后，如订阅此事件，则会收到携带最新扫描模式的回调函数。 |
| [pairDevice](arkts-connectivity-connection-pairdevice-f.md) | 主动发起与对端蓝牙设备的配对流程。使用Callback异步回调。 |
| [pairDevice](arkts-connectivity-connection-pairdevice-f.md) | 主动发起与对端蓝牙设备的配对流程。使用Promise异步回调。 |
| [pairDevice](arkts-connectivity-connection-pairdevice-f.md) | 主动发起与对端蓝牙设备的配对流程。使用Promise异步回调。 |
| [setBluetoothScanMode](arkts-connectivity-connection-setbluetoothscanmode-f.md) | 设置蓝牙扫描模式，决定本机设备是否可被连接，或者可被发现。搭配[onScanModeChange](arkts-connectivity-connection-onscanmodechange-f.md)接口使用，可实时监听蓝牙扫描模式变更事件。 |
| [setDevicePairingConfirmation](arkts-connectivity-connection-setdevicepairingconfirmation-f.md) | 收到对端蓝牙设备的配对请求事件后，确认请求结果。 |
| [setDevicePinCode](arkts-connectivity-connection-setdevicepincode-f.md) | 蓝牙配对时，弹框提示用户输入个人身份识别码（Personal identification number，PIN），调用此接口设置PIN码，完成蓝牙配对。使用Callback异步回调。 |
| [setDevicePinCode](arkts-connectivity-connection-setdevicepincode-f.md) | 蓝牙配对时，弹框提示用户输入PIN码，调用此接口设置PIN码，完成蓝牙配对。使用Promise异步回调。 |
| [setLocalName](arkts-connectivity-connection-setlocalname-f.md) | 设置本机蓝牙设备名称，不能设置为空字符串。如果设为空字符串会失败。 |
| [setRemoteDeviceName](arkts-connectivity-connection-setremotedevicename-f.md) | 设置对端蓝牙设备的名称，不能设置为空字符串。如果设为空字符串会失败。使用Promise异步回调。 |
| [startBluetoothDiscovery](arkts-connectivity-connection-startbluetoothdiscovery-f.md) | 开启蓝牙扫描，发现对端蓝牙设备。 |
| [stopBluetoothDiscovery](arkts-connectivity-connection-stopbluetoothdiscovery-f.md) | 关闭蓝牙扫描。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelPairedDevice](arkts-connectivity-connection-cancelpaireddevice-f-sys.md) | 删除配对的远程设备。使用Callback异步回调。 |
| [cancelPairedDevice](arkts-connectivity-connection-cancelpaireddevice-f-sys.md) | 删除配对的远程设备。使用Promise异步回调。 |
| [cancelPairingDevice](arkts-connectivity-connection-cancelpairingdevice-f-sys.md) | 删除正在配对中的远程设备。与cancelPairedDevice（用于删除已配对的设备）不同，本接口用于取消正在进行中的配对流程。使用Callback异步回调。 |
| [cancelPairingDevice](arkts-connectivity-connection-cancelpairingdevice-f-sys.md) | 删除正在配对中的远程设备。与cancelPairedDevice（用于删除已配对的设备）不同，本接口用于取消正在进行中的配对流程。使用Promise异步回调。 |
| [controlDeviceAction](arkts-connectivity-connection-controldeviceaction-f-sys.md) | 查找蓝牙耳机设备时，向耳机发送控制命令。使用Promise异步回调。 |
| [disconnectAllowedProfiles](arkts-connectivity-connection-disconnectallowedprofiles-f-sys.md) | 断开远端设备所有连接的profiles。使用Callback异步回调。 |
| [generateLocalOobData](arkts-connectivity-connection-generatelocaloobdata-f-sys.md) | 获取本机的带外（Out of Band, OOB）通信数据。生成的OOB数据经带外通道传输至对端设备后，对端设备可通过[pairDeviceOutOfBand](arkts-connectivity-connection-pairdeviceoutofband-f-sys.md)使用该数据发起配对流程。使用Promise异步回调。 |
| [getCarKeyDfxData](arkts-connectivity-connection-getcarkeydfxdata-f-sys.md) | 获取车钥匙维测数据，例如蓝牙车钥匙连接、配对等维测数据。 |
| [getLocalProfileUuids](arkts-connectivity-connection-getlocalprofileuuids-f-sys.md) | 获取本地设备的profile UUID。使用Callback异步回调。 |
| [getLocalProfileUuids](arkts-connectivity-connection-getlocalprofileuuids-f-sys.md) | 获取本地设备的profile UUID。使用Promise异步回调。 |
| [getRemoteDeviceType](arkts-connectivity-connection-getremotedevicetype-f-sys.md) | 获取通过setRemoteDeviceType设置的蓝牙远端设备自定义类型。使用Promise异步回调。从API version 18开始不再校验ohos.permission.ACCESS_BLUETOOTH权限。 |
| [getRemoteProductId](arkts-connectivity-connection-getremoteproductid-f-sys.md) | 获取对端蓝牙设备的Product ID。从API version 16开始不再校验ohos.permission.ACCESS_BLUETOOTH 和 ohos.permission.MANAGE_BLUETOOTH权限。 |
| [pairCredibleDevice](arkts-connectivity-connection-paircredibledevice-f-sys.md) | 向可信的远端设备发起蓝牙配对。通过非蓝牙扫描的方式（例如NFC等）获取到外设的地址，可以通过该接口发起配对。使用Callback异步回调。蓝牙配对状态通过on('bondStateChange')的回调结果获取。 |
| [pairCredibleDevice](arkts-connectivity-connection-paircredibledevice-f-sys.md) | 向可信的远端设备发起蓝牙配对。通过非蓝牙扫描的方式（例如NFC等）获取到外设的地址，可以通过该接口发起配对。使用Promise异步回调。蓝牙配对状态通过on('bondStateChange')的回调结果获取。 |
| [pairDeviceOutOfBand](arkts-connectivity-connection-pairdeviceoutofband-f-sys.md) | 通过带外（Out of Band, OOB）通信机制发起与对端蓝牙设备的配对流程。本接口所需的OobData可通过[generateLocalOobData](arkts-connectivity-connection-generatelocaloobdata-f-sys.md)生成本机OOB数据并经带外通道传输至本端后使用。使用Promise异步回调。 |
| [setCarKeyDfxData](arkts-connectivity-connection-setcarkeydfxdata-f-sys.md) | 把车钥匙执行开卡、删卡操作的事件通知蓝牙，以便蓝牙模块记录相应的维测（DFX）数据用于后续问题定位。 |
| [setRemoteDeviceType](arkts-connectivity-connection-setremotedevicetype-f-sys.md) | 设置蓝牙远端设备自定义类型，适用于蓝牙设置或设备管理应用中按设备类型（如汽车、耳机、助听器等）进行分类展示或差异化处理的场景。使用Promise异步回调。 |
| [startPairOutOfBand](arkts-connectivity-connection-startpairoutofband-f-sys.md) | 使用带外机制开始与特定的远程蓝牙设备配对。该函数为异步函数，通过监听bondStateChange事件获取配对状态。如果没有使用p192Data和p256Data，函数调用将失败。如果同时使用p192Data和p256Data，则以p256Data生效。 |
| [updateCloudBluetoothDevice](arkts-connectivity-connection-updatecloudbluetoothdevice-f-sys.md) | 更新云设备到蓝牙设置，适用于换机恢复或跨设备同步场景下，将云端已配对设备信息同步到本地蓝牙设置中。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AclStateResult](arkts-connectivity-connection-aclstateresult-i.md) | 描述ACL连接状态的参数结构。 |
| [BatteryInfo](arkts-connectivity-connection-batteryinfo-i.md) | 描述设备的电量信息。 |
| [BondStateParam](arkts-connectivity-connection-bondstateparam-i.md) | 描述配对状态结果的参数结构。 |
| [DeviceClass](arkts-connectivity-connection-deviceclass-i.md) | 描述蓝牙设备的类型。 |
| [DiscoveryResult](arkts-connectivity-connection-discoveryresult-i.md) | 扫描到设备后，上报的扫描结果。 |
| [PinRequiredParam](arkts-connectivity-connection-pinrequiredparam-i.md) | 描述配对请求的参数结构。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BatteryInfo](arkts-connectivity-connection-batteryinfo-i-sys.md) | 描述设备的电量信息。 |
| [ControlDeviceActionParams](arkts-connectivity-connection-controldeviceactionparams-i-sys.md) | 控制命令的配置参数。 |
| [OobData](arkts-connectivity-connection-oobdata-i-sys.md) | 用于OOB配对的数据对象。 |
| [PinRequiredParam](arkts-connectivity-connection-pinrequiredparam-i-sys.md) | 描述配对请求的参数结构。 |
| [TrustedPairedDevice](arkts-connectivity-connection-trustedpaireddevice-i-sys.md) | 云设备信息。 |
| [TrustedPairedDevices](arkts-connectivity-connection-trustedpaireddevices-i-sys.md) | 云设备列表。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AclState](arkts-connectivity-connection-aclstate-e.md) | 枚举，表示ACL连接状态。 |
| [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 枚举，表示设备传输类型。 |
| [BondState](arkts-connectivity-connection-bondstate-e.md) | 枚举，配对状态。 |
| [DeviceChargeState](arkts-connectivity-connection-devicechargestate-e.md) | 枚举，表示设备当前的充电状态。 |
| [HashAlgorithmType](arkts-connectivity-connection-hashalgorithmtype-e.md) | 枚举，表示哈希算法类型。 |
| [ScanMode](arkts-connectivity-connection-scanmode-e.md) | 枚举，表示扫描模式。该模式决定设备是否可被发现或可被连接。 |
| [UnbondCause](arkts-connectivity-connection-unbondcause-e.md) | 枚举，配对失败原因。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CarKeyActionType](arkts-connectivity-connection-carkeyactiontype-e-sys.md) | 枚举，车钥匙执行的操作。 |
| [ControlObject](arkts-connectivity-connection-controlobject-e-sys.md) | 枚举，控制对象。 |
| [ControlType](arkts-connectivity-connection-controltype-e-sys.md) | 枚举，控制类型。 |
| [ControlTypeValue](arkts-connectivity-connection-controltypevalue-e-sys.md) | 枚举，控制动作。 |
| [DeviceRole](arkts-connectivity-connection-devicerole-e-sys.md) | 枚举，蓝牙设备在连接过程中的角色。 |
| [DeviceType](arkts-connectivity-connection-devicetype-e-sys.md) | 枚举，蓝牙远程设备的自定义类型。 |
| [PinType](arkts-connectivity-connection-pintype-e-sys.md) | 枚举，蓝牙配对类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-connection-bluetoothaddress-t.md) | 描述蓝牙设备地址信息的参数结构，包括地址与地址类型。 |
| [MajorClass](arkts-connectivity-connection-majorclass-t.md) | 蓝牙设备的主要类型。蓝牙标准协议字段。 |
| [MajorMinorClass](arkts-connectivity-connection-majorminorclass-t.md) | 蓝牙设备的子类型，在[MajorClass](arkts-connectivity-constant-majorclass-e.md)基础上进一步细分的类型。蓝牙标准协议字段。 |
| [ProfileConnectionState](arkts-connectivity-connection-profileconnectionstate-t.md) | 蓝牙设备的Profile协议连接状态。Profile协议包括A2DP（Advanced Audio Distribution Profile）、HFP（Hands-Free Profile）和HID（Human Interface Device）等。 |
| [ProfileId](arkts-connectivity-connection-profileid-t.md) | 枚举，蓝牙Profile协议。 |
| [ProfileUuids](arkts-connectivity-connection-profileuuids-t.md) | 蓝牙Profile协议的UUID。 |
