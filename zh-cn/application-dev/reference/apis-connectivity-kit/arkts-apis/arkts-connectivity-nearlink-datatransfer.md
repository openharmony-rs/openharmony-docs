# @ohos.nearlink.dataTransfer(星闪数传能力)

本模块提供了星闪数据传输功能，包括端口通道管理、连接管理、数据收发、连接状态查询与订阅等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [connect](arkts-connectivity-datatransfer-connect-f.md) | 连接远端设备。使用Promise异步回调。 |
| [createPort](arkts-connectivity-datatransfer-createport-f.md) | 注册端口通道。端口通道注册后方可用于连接远端设备，不再使用时需通过[dataTransfer.destroyPort](arkts-connectivity-datatransfer-destroyport-f.md)销毁。 |
| [destroyPort](arkts-connectivity-datatransfer-destroyport-f.md) | 销毁端口通道。 |
| [disconnect](arkts-connectivity-datatransfer-disconnect-f.md) | 断连远端设备。需在通过[dataTransfer.connect](arkts-connectivity-datatransfer-connect-f.md)成功建立连接后调用，用于断开已建立的远端设备连接。使用Promise异步回调。 |
| [getConnectionState](arkts-connectivity-datatransfer-getconnectionstate-f.md) | 获取与远端设备之间的端口通道连接状态。 |
| [offConnectionStateChanged](arkts-connectivity-datatransfer-offconnectionstatechanged-f.md) | 取消订阅端口通道连接状态变更事件。使用callback异步回调。 |
| [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md) | 取消订阅端口通道数据接收事件。使用callback异步回调。 |
| [onConnectionStateChanged](arkts-connectivity-datatransfer-onconnectionstatechanged-f.md) | 订阅端口通道连接状态变更事件。使用callback异步回调。 |
| [onReadData](arkts-connectivity-datatransfer-onreaddata-f.md) | 订阅端口通道数据接收事件。使用callback异步回调。 |
| [writeData](arkts-connectivity-datatransfer-writedata-f.md) | 通过设备地址和UUID向远端设备发送数据。使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | 发起端口连接的参数。 |
| [ConnectionResult](arkts-connectivity-datatransfer-connectionresult-i.md) | 与远端设备端口连接参数的协商结果 |
| [ConnectionStateParams](arkts-connectivity-datatransfer-connectionstateparams-i.md) | 获取端口通道连接状态所需参数。 |
| [DataParams](arkts-connectivity-datatransfer-dataparams-i.md) | 端口数据发送和接收的参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TransferMode](arkts-connectivity-datatransfer-transfermode-e.md) | 表示和远端设备的数据传输模式，为枚举值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ConnectionState](arkts-connectivity-datatransfer-connectionstate-t.md) | 表示和远端设备的连接状态，为枚举值。 |
