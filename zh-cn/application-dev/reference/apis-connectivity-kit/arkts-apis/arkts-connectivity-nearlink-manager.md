# @ohos.nearlink.manager(星闪基础管理能力)

本模块提供了星闪基础管理能力，包括打开/关闭星闪、获取本机MAC地址、设置连接模式等能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLocalName](arkts-connectivity-manager-getlocalname-f.md) | 查询本机星闪名称。 |
| [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md) | 获取与当前设备配对的设备列表。 |
| [getState](arkts-connectivity-manager-getstate-f.md) | 查询星闪开关状态。 |
| [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) | 查询当前设备是否支持星闪服务。 |
| [offStateChange](arkts-connectivity-manager-offstatechange-f.md) | 取消订阅星闪开关状态变化事件。使用callback异步回调。 |
| [onStateChange](arkts-connectivity-manager-onstatechange-f.md) | 订阅星闪开关状态变化事件。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disable](arkts-connectivity-manager-disable-f-sys.md) | 关闭星闪。 |
| [enable](arkts-connectivity-manager-enable-f-sys.md) | 打开星闪。 |
| [factoryReset](arkts-connectivity-manager-factoryreset-f-sys.md) | 恢复出厂设置。使用Promise异步回调。 |
| [getLocalAddress](arkts-connectivity-manager-getlocaladdress-f-sys.md) | 查询本机MAC地址。 |
| [setConnectionMode](arkts-connectivity-manager-setconnectionmode-f-sys.md) | 设置连接模式。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | 星闪的开关状态，为枚举值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | 连接模式的枚举值。 |
<!--DelEnd-->
