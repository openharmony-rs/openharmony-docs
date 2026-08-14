# @ohos.nearlink.dataTransfer

提供操作和管理星闪数据传输的方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace dataTransfer--><!--Device-unnamed-declare namespace dataTransfer-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [connect](arkts-connectivity-datatransfer-connect-f.md#connect) | 连接服务端。如果连接成功，则可以向服务端发送数据。 |
| [createPort](arkts-connectivity-datatransfer-createport-f.md#createPort) | 通过UUID创建可以接收数据的星闪端口。 |
| [destroyPort](arkts-connectivity-datatransfer-destroyport-f.md#destroyPort) | 根据UUID销毁监听端口并释放相关资源。 |
| [disconnect](arkts-connectivity-datatransfer-disconnect-f.md#disconnect) | 断开或停止与服务端的连接。 |
| [getConnectionState](arkts-connectivity-datatransfer-getconnectionstate-f.md#getConnectionState) | 获取数据传输的连接状态。 |
| [offConnectionStateChanged](arkts-connectivity-datatransfer-offconnectionstatechanged-f.md#offConnectionStateChanged) | 取消订阅连接状态变更事件。 |
| [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md#offReadData) | 取消订阅从端口读取数据的事件。 |
| [onConnectionStateChanged](arkts-connectivity-datatransfer-onconnectionstatechanged-f.md#onConnectionStateChanged) | 订阅连接状态变化事件。 只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。 |
| [onReadData](arkts-connectivity-datatransfer-onreaddata-f.md#onReadData) | 订阅从端口读取数据事件。 只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。 |
| [writeData](arkts-connectivity-datatransfer-writedata-f.md#writeData) | 根据地址和UUID写入数据。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | 连接参数。 |
| [ConnectionResult](arkts-connectivity-datatransfer-connectionresult-i.md) | 连接结果的参数说明。 |
| [ConnectionStateParams](arkts-connectivity-datatransfer-connectionstateparams-i.md) | 获取连接状态所需的参数。 |
| [DataParams](arkts-connectivity-datatransfer-dataparams-i.md) | 数据参数说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TransferMode](arkts-connectivity-datatransfer-transfermode-e.md) | 数据传输模式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ConnectionState](arkts-connectivity-datatransfer-connectionstate-t.md) | 连接状态。 |

