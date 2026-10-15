# @ohos.nearlink.manager(星闪基础管理能力)

本模块提供了星闪基础管理能力，包括打开/关闭星闪、获取本机MAC地址、设置连接模式等能力。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace manager--><!--Device-unnamed-declare namespace manager-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLocalName](arkts-connectivity-manager-getlocalname-f.md#getlocalname) | 查询本机星闪名称。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md#getpaireddevices) | 获取与当前设备配对的设备列表。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [getState](arkts-connectivity-manager-getstate-f.md#getstate) | 查询星闪开关状态。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [isFrameType4Supported](arkts-connectivity-manager-isframetype4supported-f.md#isframetype4supported) | 查询当前设备是否支持帧类型4。 |
| [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md#isnearlinksupported) | 查询当前设备是否支持星闪服务。 |
| [offStateChange](arkts-connectivity-manager-offstatechange-f.md#offstatechange) | 取消订阅星闪开关状态变化事件。使用callback异步回调。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [onStateChange](arkts-connectivity-manager-onstatechange-f.md#onstatechange) | 订阅星闪开关状态变化事件。使用callback异步回调。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disable](arkts-connectivity-manager-disable-f-sys.md#disable) | 关闭星闪。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [enable](arkts-connectivity-manager-enable-f-sys.md#enable) | 打开星闪。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [enableWithOptions](arkts-connectivity-manager-enablewithoptions-f-sys.md#enablewithoptions) | 以指定选项打开星闪。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [factoryReset](arkts-connectivity-manager-factoryreset-f-sys.md#factoryreset) | 恢复出厂设置。使用Promise异步回调。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [getLocalAddress](arkts-connectivity-manager-getlocaladdress-f-sys.md#getlocaladdress) | 查询本机MAC地址。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
| [setConnectionMode](arkts-connectivity-manager-setconnectionmode-f-sys.md#setconnectionmode) | 设置连接模式。使用Promise异步回调。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EnableOptions](arkts-connectivity-manager-enableoptions-i-sys.md) | 打开星闪时使用的选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | 星闪的开关状态，为枚举值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AutoConnectPolicy](arkts-connectivity-manager-autoconnectpolicy-e-sys.md) | 表示打开星闪时的自动连接策略，为枚举值。 |
| [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | 连接模式的枚举值。 |
<!--DelEnd-->
