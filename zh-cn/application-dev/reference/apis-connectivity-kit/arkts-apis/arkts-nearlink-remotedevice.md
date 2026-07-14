# @ohos.nearlink.remoteDevice

提供与远端设备的配对、连接等交互方式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createRemoteDevice](arkts-connectivity-createremotedevice-f.md#createremotedevice-1) | 创建远端设备实例。 |
| [offAcbStateChange](arkts-connectivity-offacbstatechange-f.md#offacbstatechange-1) | 取消订阅星闪 ACB连接状态更改事件。 |
| [offConnectionStateChange](arkts-connectivity-offconnectionstatechange-f.md#offconnectionstatechange-1) | 取消订阅星闪连接状态更改事件。 |
| [offPairingStateChange](arkts-connectivity-offpairingstatechange-f.md#offpairingstatechange-1) | 取消订阅星闪配对状态更改事件。 |
| [onAcbStateChange](arkts-connectivity-onacbstatechange-f.md#onacbstatechange-1) | 订阅NearLink ACB连接状态变化事件。ACB采用异步双向链路。&gt; **说明**&gt; 如果该用户具有ohos.permission.GET_NEARLINK_PEER_MAC权限，则真实设备地址为&gt; 返回。&gt; 否则，将返回一个随机的设备地址。只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。 |
| [onConnectionStateChange](arkts-connectivity-onconnectionstatechange-f.md#onconnectionstatechange-1) | 订阅星闪连接状态更改事件。如果用户有ohos.permission.GET_NEARLINK_PEER_MAC权限，则返回真实设备地址。否则返回一个随机的设备地址。只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。 |
| [onPairingStateChange](arkts-connectivity-onpairingstatechange-f.md#onpairingstatechange-1) | 订阅NearLink配对状态变更事件。只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offPairingRequest](arkts-connectivity-offpairingrequest-f-sys.md#offpairingrequest-1) | 取消订阅来自远端星闪设备的配对请求事件。 |
| [onPairingRequest](arkts-connectivity-onpairingrequest-f-sys.md#onpairingrequest-1) | 订阅来自远程NearLink设备的配对请求事件。如果用户被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AcbStateParam](arkts-connectivity-acbstateparam-i.md) | ACB连接状态参数。 |
| [ConnectionStateParam](arkts-connectivity-connectionstateparam-i.md) | 连接状态参数。 |
| [DeviceInformation](arkts-connectivity-deviceinformation-i.md) | 描述远端设备信息。 |
| [PairingRequestParam](arkts-connectivity-pairingrequestparam-i.md) | 配对请求参数说明。 |
| [PairingStateParam](arkts-connectivity-pairingstateparam-i.md) | 配对状态参数。 |
| [RemoteDevice](arkts-connectivity-remotedevice-i.md) | 远程设备操作方法。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceModel](arkts-connectivity-devicemodel-i-sys.md) | 远程设备的型号信息。 |
| [RemoteDevice](arkts-connectivity-remotedevice-i-sys.md) | 远程设备操作方法。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ConnectionReason](arkts-connectivity-connectionreason-e.md) | 连接原因的枚举。 |
| [PairingReason](arkts-connectivity-pairingreason-e.md) | 配对原因的枚举。 |
| [PairingType](arkts-connectivity-pairingtype-e.md) | 配对类型的枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AcbState](arkts-connectivity-acbstate-t.md) | ACB（异步面向连接的双向）连接状态。 |
| [ConnectionState](arkts-connectivity-connectionstate-t.md) | 连接状态。 |
| [DeviceClass](arkts-connectivity-deviceclass-t.md) | 设备类型。 |
| [PairingState](arkts-connectivity-pairingstate-t.md) | 配对状态。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionInterval](arkts-connectivity-connectioninterval-t-sys.md) | 连接间隔。 |
<!--DelEnd-->

