# @ohos.bluetooth.hid(蓝牙hid模块)

本模块提供基于人机接口协议（Human Interface Device Profile，HID）技术的蓝牙人机交互能力，支持获取连接状态等方法。

当本端设备被注册为HID设备的角色时，可以使用[HidDeviceProfile](arkts-connectivity-hid-hiddeviceprofile-i.md)相关接口，且仅支持与传统蓝牙类型设备连接和交互。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createHidDeviceProfile](arkts-connectivity-hid-createhiddeviceprofile-f.md) | 创建蓝牙HID Device实例。通过该实例可使用本端作为HID Device的接口，如：获取和其他设备间的蓝牙HID连接状态。 |
| [createHidHostProfile](arkts-connectivity-hid-createhidhostprofile-f.md) | 创建蓝牙HID Host实例。通过该实例可使用本端作为HID Host的接口，如：获取和其他设备间的蓝牙HID连接状态。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GetReportData](arkts-connectivity-hid-getreportdata-i.md) | 描述HID主机向HID设备发送的GET_REPORT传输请求事件的信息。 |
| [HidDeviceProfile](arkts-connectivity-hid-hiddeviceprofile-i.md) | 该实例表示蓝牙HID通信中的HID Device角色。 |
| [HidDeviceQos](arkts-connectivity-hid-hiddeviceqos-i.md) | 描述HID设备服务质量（Qos）参数。该结构定义了HID数据传输通道的流量控制、延迟保证和可靠性策略，用于优化蓝牙传输性能，确保设备的实时响应性。 |
| [HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md) | 描述HID设备在服务发现协议（SDP）中的服务注册配置。该结构定义了HID设备的身份标识、能力描述和协议特征，是HID主机发现、识别和连接HID设备的关键参数。 |
| [InterruptData](arkts-connectivity-hid-interruptdata-i.md) | 描述从主机收到的中断数据。 |
| [ProtocolData](arkts-connectivity-hid-protocoldata-i.md) | 描述从HID主机接收的通信协议数据。 |
| [SetReportData](arkts-connectivity-hid-setreportdata-i.md) | 描述HID主机向HID设备发送的SET_REPORT传输请求事件的信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HidHostProfile](arkts-connectivity-hid-hidhostprofile-i-sys.md) | HidHostProfile类提供蓝牙HID设备的连接和断开等管理功能，适用于系统应用中管理蓝牙HID设备的场景。使用HidHostProfile方法之前需要创建该类的实例进行操作，通过[createHidHostProfile()](arkts-connectivity-hid-createhidhostprofile-f.md)方法构造此实例。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ErrorReason](arkts-connectivity-hid-errorreason-e.md) | 枚举，描述错误原因。 |
| [ProtocolType](arkts-connectivity-hid-protocoltype-e.md) | 枚举，HID设备与主机的通信协议类型。 |
| [ReportType](arkts-connectivity-hid-reporttype-e.md) | 枚举，报告类型。 |
| [ServiceType](arkts-connectivity-hid-servicetype-e.md) | 枚举，描述HID设备与主机之间连接的服务类型。 |
| [Subclass](arkts-connectivity-hid-subclass-e.md) | 枚举，HID设备的具体类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-hid-baseprofile-t.md) | 基础Profile接口定义，提供订阅连接状态和获取连接状态等公共能力。 |
| [BluetoothAddress](arkts-connectivity-hid-bluetoothaddress-t.md) | 描述蓝牙设备地址信息的参数结构，包括地址与地址类型。 |
