# @ohos.nearlink.manager

提供管理星闪设备的方法。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLocalName](arkts-connectivity-getlocalname-f.md#getlocalname-1) | 获取本地设备的名称。 |
| [getPairedDevices](arkts-connectivity-getpaireddevices-f.md#getpaireddevices-1) | 获取已与当前设备配对的设备列表。如果用户有ohos.permission.GET_NEARLINK_PEER_MAC权限，则返回真实设备地址。否则，返回随机的设备地址 |
| [getState](arkts-connectivity-getstate-f.md#getstate-1) | 获取星闪状态。 |
| [isNearLinkSupported](arkts-connectivity-isnearlinksupported-f.md#isnearlinksupported-1) | 检查当前设备是否支持星闪。 |
| [offStateChange](arkts-connectivity-offstatechange-f.md#offstatechange-1) | 取消订阅状态变更事件。 |
| [onStateChange](arkts-connectivity-onstatechange-f.md#onstatechange-1) | 订阅状态变更事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disable](arkts-connectivity-disable-f-sys.md#disable-1) | 关闭星闪。 |
| [enable](arkts-connectivity-enable-f-sys.md#enable-1) | 开启星闪。 |
| [factoryReset](arkts-connectivity-factoryreset-f-sys.md#factoryreset-1) | 恢复星闪设置。 |
| [getLocalAddress](arkts-connectivity-getlocaladdress-f-sys.md#getlocaladdress-1) | 获取本端设备的MAC地址。 |
| [setConnectionMode](arkts-connectivity-setconnectionmode-f-sys.md#setconnectionmode-1) | 设置设备的NearLink连接模式。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NearlinkState](arkts-connectivity-nearlinkstate-e.md) | 星闪状态的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionMode](arkts-connectivity-connectionmode-e-sys.md) | 连接模式的枚举。 |
<!--DelEnd-->

