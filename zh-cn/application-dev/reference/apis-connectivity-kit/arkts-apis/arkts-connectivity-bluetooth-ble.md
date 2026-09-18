# @ohos.bluetooth.ble(蓝牙ble模块)

本模块提供了基于低功耗蓝牙（Bluetooth Low Energy，BLE）技术的蓝牙能力，支持发起BLE扫描、发送BLE广播报文、以及基于通用属性协议（Generic Attribute Profile，GATT）的连接和传输数据。适用于智能穿戴设备、健康监测、物联网设备互联等低功耗短距离无线通信场景，有助于降低设备功耗、延长续航时间。

接口中涉及的UUID服务，可以通过工具函数[util.generateRandomUUID](../../apis-arkts/arkts-apis/arkts-arkts-util-generaterandomuuid-f.md)生成。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createBleScanner](arkts-connectivity-ble-createblescanner-f.md) | 创建一个[BleScanner](arkts-connectivity-ble-blescanner-i.md)实例对象，可用于发起或停止BLE扫描等流程。 |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | 创建[GattClientDevice](arkts-connectivity-ble-gattclientdevice-i.md)实例，表示GATT连接中的client端。 |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | 创建[GattClientDevice](arkts-connectivity-ble-gattclientdevice-i.md)实例，表示GATT连接中的client端，可通过[GattSetting](arkts-connectivity-ble-gattsetting-i.md)设置GATT连接参数。 |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md) | 创建[GattServer](arkts-connectivity-ble-gattserver-i.md)实例，表示GATT连接中的server端。 |
| [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md) | 停止指定标识的BLE广播。使用Callback异步回调。 |
| [disableAdvertising](arkts-connectivity-ble-disableadvertising-f.md) | 停止指定标识的BLE广播。使用Promise异步回调。 |
| [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) | 重新启动指定标识的BLE广播。使用Callback异步回调。 |
| [enableAdvertising](arkts-connectivity-ble-enableadvertising-f.md) | 重新启动指定标识的BLE广播。使用Promise异步回调。 |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | 获取和本机设备已连接GATT的BLE设备集合。 |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | 根据指定的本机设备Profile协议类型，获取和本机设备已连接GATT的BLE设备集合。 |
| off | 取消订阅BLE广播状态。广播停止或启动将不再收到通知。 |
| [off](arkts-connectivity-ble-off-f.md#offbledevicefind) | 取消订阅BLE设备扫描结果上报事件。 |
| on | 订阅BLE广播状态。使用Callback异步回调。 |
| [on](arkts-connectivity-ble-on-f.md#onbledevicefind) | 订阅BLE设备扫描结果上报事件。使用Callback异步回调。 |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | 开始发送BLE广播报文。 |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | 首次启动发送BLE广播报文。使用Callback异步回调。 |
| [startAdvertising](arkts-connectivity-ble-startadvertising-f.md) | 首次启动发送BLE广播报文。使用Promise异步回调。 |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md) | 发起BLE扫描流程。 |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | 停止发送BLE广播报文。 |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | 完全停止发送BLE广播。使用Callback异步回调。 |
| [stopAdvertising](arkts-connectivity-ble-stopadvertising-f.md) | 完全停止发送BLE广播。使用Promise异步回调。 |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md) | 停止BLE扫描流程。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md) | 描述BLE广播报文数据内容，也可以用作回复扫描请求的广播报文数据内容。支持传统广播和扩展广播，传统广播报文最大长度为31个字节，扩展广播报文最大长度由蓝牙芯片能力决定。若超出最大长度限制，会导致启动广播失败。 |
| [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md) | 描述BLE广播的发送参数。 |
| [AdvertisingDisableParams](arkts-connectivity-ble-advertisingdisableparams-i.md) | 停止指定标识的BLE广播时设置的参数。 |
| [AdvertisingEnableParams](arkts-connectivity-ble-advertisingenableparams-i.md) | 启动指定标识的BLE广播时设置的参数。 |
| [AdvertisingParams](arkts-connectivity-ble-advertisingparams-i.md) | 首次启动BLE广播时设置的参数。 |
| [AdvertisingStateChangeInfo](arkts-connectivity-ble-advertisingstatechangeinfo-i.md) | 描述BLE广播启动、停止的状态信息。 |
| [BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md) | GATT特征值结构定义，是服务[GattService](arkts-connectivity-ble-gattservice-i.md)的核心数据单元。 |
| [BLEConnectionChangeState](arkts-connectivity-ble-bleconnectionchangestate-i.md) | 描述GATT profile协议连接状态。 |
| [BLEDescriptor](arkts-connectivity-ble-bledescriptor-i.md) | GATT描述符结构定义，是特征值[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)的数据单元，用于描述特征值的附加信息和属性。 |
| [BleScanner](arkts-connectivity-ble-blescanner-i.md) | BLE扫描类，提供了扫描相关的操作方法。 |
| [CharacteristicReadRequest](arkts-connectivity-ble-characteristicreadrequest-i.md) | 描述server端订阅client端读特征值请求事件后，接收到的事件参数结构。 |
| [CharacteristicWriteRequest](arkts-connectivity-ble-characteristicwriterequest-i.md) | 描述server端订阅client端写特征值请求事件后，接收到的事件参数结构。 |
| [DescriptorReadRequest](arkts-connectivity-ble-descriptorreadrequest-i.md) | 描述server端订阅client端读描述符请求事件后，接收到的事件参数结构。 |
| [DescriptorWriteRequest](arkts-connectivity-ble-descriptorwriterequest-i.md) | 描述server端订阅client端写描述符请求事件后，接收到的事件参数结构。 |
| [GattClientDevice](arkts-connectivity-ble-gattclientdevice-i.md) | GATT客户端类，提供了和服务端进行连接和数据传输等操作方法。 |
| [GattPermissions](arkts-connectivity-ble-gattpermissions-i.md) | 描述读写GATT特征值或描述符需具备的权限。 |
| [GattProperties](arkts-connectivity-ble-gattproperties-i.md) | 描述GATT特征值支持的属性。决定了特征值内容和描述符如何被使用和访问。 |
| [GattServer](arkts-connectivity-ble-gattserver-i.md) | GATT通信中的服务端类。 |
| [GattService](arkts-connectivity-ble-gattservice-i.md) | GATT服务结构定义，可包含多个特征值[BLECharacteristic](arkts-connectivity-ble-blecharacteristic-i.md)和依赖的其他服务。 |
| [GattSetting](arkts-connectivity-ble-gattsetting-i.md) | 描述GATT连接的参数。 |
| [ManufactureData](arkts-connectivity-ble-manufacturedata-i.md) | 描述BLE广播报文中制造商数据内容。 |
| [NotifyCharacteristic](arkts-connectivity-ble-notifycharacteristic-i.md) | 描述server端特征值发生变化时，server端发送特征值通知的参数结构。 |
| [PhyValue](arkts-connectivity-ble-phyvalue-i.md) | 连接链路的物理通道类型配置参数。 |
| [ScanFilter](arkts-connectivity-ble-scanfilter-i.md) | 扫描BLE广播的过滤条件，只有符合该条件的广播报文才会上报。 |
| [ScanOptions](arkts-connectivity-ble-scanoptions-i.md) | BLE扫描的配置参数。 |
| [ScanReport](arkts-connectivity-ble-scanreport-i.md) | 上报的扫描数据。 |
| [ScanResult](arkts-connectivity-ble-scanresult-i.md) | 扫描到符合过滤条件的广播报文后，上报的扫描数据。 |
| [ServerResponse](arkts-connectivity-ble-serverresponse-i.md) | 描述server端回复client端读或者写请求的响应参数结构。 |
| [ServiceData](arkts-connectivity-ble-servicedata-i.md) | 描述BLE广播报文中的服务数据内容。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GattClientDevice](arkts-connectivity-ble-gattclientdevice-i-sys.md) | GATT客户端类，提供了和服务端进行连接和数据传输等操作方法。 |
| [GattRspContext](arkts-connectivity-ble-gattrspcontext-i-sys.md) | client端调用[writeCharacteristicValueWithContext](arkts-connectivity-ble-gattclientdevice-i-sys.md#writecharacteristicvaluewithcontext)等接口并接收到server端的回复消息后，蓝牙子系统上报给应用的信息。 |
| [ScanEnhanceMode](arkts-connectivity-ble-scanenhancemode-i-sys.md) | The enum of gatt characteristic write type |
| [ScanFilter](arkts-connectivity-ble-scanfilter-i-sys.md) | 扫描BLE广播的过滤条件，只有符合该条件的广播报文才会上报。 |
| [ScanOptions](arkts-connectivity-ble-scanoptions-i-sys.md) | BLE扫描的配置参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AdvertisingState](arkts-connectivity-ble-advertisingstate-e.md) | 枚举，不同操作对应的BLE广播状态。 |
| [BlePhy](arkts-connectivity-ble-blephy-e.md) | 枚举，连接与广播的物理通道类型。 |
| [BleProfile](arkts-connectivity-ble-bleprofile-e.md) | 枚举，指定当前设备的Profile协议类型。 |
| [CodedPhyMode](arkts-connectivity-ble-codedphymode-e.md) | 枚举，BLE_PHY_CODED类型下的编码方式。 |
| [ConnectionParam](arkts-connectivity-ble-connectionparam-e.md) | 枚举，连接参数类型。 |
| [GattDisconnectReason](arkts-connectivity-ble-gattdisconnectreason-e.md) | 枚举，指定GATT链路断开的原因。 |
| [GattWriteType](arkts-connectivity-ble-gattwritetype-e.md) | 枚举，写入特征值的方式（不同的取值，对端蓝牙设备的表现不一样）。 |
| [MatchMode](arkts-connectivity-ble-matchmode-e.md) | 枚举，硬件过滤匹配模式。 |
| [PhyType](arkts-connectivity-ble-phytype-e.md) | 枚举，指定扫描过程中接收BLE广播报文的物理通道。 |
| [ScanDuty](arkts-connectivity-ble-scanduty-e.md) | 枚举，扫描模式，表示不同的扫描性能和功耗情况。 |
| [ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md) | 枚举，扫描结果上报模式。 |
| [ScanReportType](arkts-connectivity-ble-scanreporttype-e.md) | 枚举，扫描结果上报类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EnhanceMode](arkts-connectivity-ble-enhancemode-e-sys.md) | 枚举，高性能扫描模式配置。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BluetoothAddress](arkts-connectivity-ble-bluetoothaddress-t.md) | 描述蓝牙设备地址信息的参数结构，包括地址与地址类型。 |
| [BluetoothTransport](arkts-connectivity-ble-bluetoothtransport-t.md) | 表示远端设备的传输类型。 |
| [ProfileConnectionState](arkts-connectivity-ble-profileconnectionstate-t.md) | 蓝牙设备的Profile协议连接状态。 |
