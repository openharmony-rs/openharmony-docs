# @ohos.nearlink.remoteDevice(星闪远端设备连接能力)

本模块提供了星闪远端设备的连接与管理能力，包括连接与断开远端设备、可信配对与确认、调整连接间隔、订阅配对请求等。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createRemoteDevice(星闪远端设备连接能力)](arkts-connectivity-remotedevice-createremotedevice-f.md) | 创建远端设备实例。 |
| [offAcbStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-offacbstatechange-f.md) | 取消订阅逻辑链路连接状态变化事件。使用callback异步回调。 |
| [offConnectionStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-offconnectionstatechange-f.md) | 取消订阅连接状态变化事件。使用callback异步回调。 |
| [offPairingStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-offpairingstatechange-f.md) | 取消订阅配对状态变化事件。使用callback异步回调。 |
| [onAcbStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-onacbstatechange-f.md) | 订阅逻辑链路连接状态变化事件。使用callback异步回调。适用于需要在逻辑链路建立或断开时触发相应处理的场景，如数据传输前的链路就绪检查或断连后的资源清理。与 [remoteDevice.onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md) 监听设备层级连接状态不同，本接口监听逻辑链路层级的连接状态。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。 |
| [onConnectionStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-onconnectionstatechange-f.md) | 订阅连接状态变化事件。使用callback异步回调。与 [remoteDevice.onAcbStateChange](arkts-connectivity-remotedevice-onacbstatechange-f.md)监听逻辑链路层级连接状态 不同，本接口监听设备层级的连接状态变化。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。 |
| [onPairingStateChange(星闪远端设备连接能力)](arkts-connectivity-remotedevice-onpairingstatechange-f.md) | 订阅配对状态变化事件。使用callback异步回调。应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offPairingRequest(星闪远端设备连接能力)](arkts-connectivity-remotedevice-offpairingrequest-f-sys.md) | 取消订阅来自远端星闪设备的配对请求事件。 |
| [onPairingRequest(星闪远端设备连接能力)](arkts-connectivity-remotedevice-onpairingrequest-f-sys.md) | 订阅来自远程NearLink设备的配对请求事件。 如果用户被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。 回调返回真实设备地址，否则返回随机设备地址只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。 如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。 回调返回真实设备地址，否则返回随机设备地址。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AcbStateParam(星闪远端设备连接能力)](arkts-connectivity-remotedevice-acbstateparam-i.md) | 订阅的逻辑链路连接状态变化事件上报结果。 |
| [ConnectionStateParam(星闪远端设备连接能力)](arkts-connectivity-remotedevice-connectionstateparam-i.md) | 连接状态参数。 |
| [DeviceInformation(星闪远端设备连接能力)](arkts-connectivity-remotedevice-deviceinformation-i.md) | 描述远端设备信息。 |
| [PairingRequestParam(星闪远端设备连接能力)](arkts-connectivity-remotedevice-pairingrequestparam-i.md) | 配对请求参数说明。 |
| [PairingStateParam(星闪远端设备连接能力)](arkts-connectivity-remotedevice-pairingstateparam-i.md) | 配对状态参数。 |
| [RemoteDevice(星闪远端设备连接能力)](arkts-connectivity-remotedevice-remotedevice-i.md) | 提供远端设备的操作方法，使用前需要使用[remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md)方法创建一个远端设备 [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md)实例。一个设备只需要创建一次，无需多次创建。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceModel(星闪远端设备连接能力)](arkts-connectivity-remotedevice-devicemodel-i-sys.md) | 描述远端设备的型号信息。 |
| [RemoteDevice(星闪远端设备连接能力)](arkts-connectivity-remotedevice-remotedevice-i-sys.md) | 提供远端设备的操作方法，使用前需要使用[remoteDevice.createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md)方法创建一个远端设备 [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md)实例。一个设备只需要创建一次，无需多次创建。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConnectionReason(星闪远端设备连接能力)](arkts-connectivity-remotedevice-connectionreason-e.md) | 连接原因的枚举。 |
| [PairingReason(星闪远端设备连接能力)](arkts-connectivity-remotedevice-pairingreason-e.md) | 配对原因的枚举。 |
| [PairingType(星闪远端设备连接能力)](arkts-connectivity-remotedevice-pairingtype-e.md) | 星闪配对类型，为枚举值。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AcbState(星闪远端设备连接能力)](arkts-connectivity-remotedevice-acbstate-t.md) | 表示和远端设备的逻辑链路连接状态，为枚举值。 |
| [ConnectionState(星闪远端设备连接能力)](arkts-connectivity-remotedevice-connectionstate-t.md) | 表示和远端设备的连接状态，为枚举值。 |
| [DeviceClass(星闪远端设备连接能力)](arkts-connectivity-remotedevice-deviceclass-t.md) | 表示设备类型，为枚举值。 |
| [PairingState(星闪远端设备连接能力)](arkts-connectivity-remotedevice-pairingstate-t.md) | 表示和远端设备的配对状态，为枚举值。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionInterval(星闪远端设备连接能力)](arkts-connectivity-remotedevice-connectioninterval-t-sys.md) | 表示连接间隔，为枚举值。 |
<!--DelEnd-->
