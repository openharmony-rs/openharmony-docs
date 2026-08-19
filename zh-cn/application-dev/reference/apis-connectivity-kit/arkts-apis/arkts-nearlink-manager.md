# @ohos.nearlink.manager

提供管理星闪设备的方法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [getLocalName](arkts-connectivity-manager-getlocalname-f.md) | 获取本地设备的名称。 |
| [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md) | 获取已与当前设备配对的设备列表。 如果用户有ohos.permission.GET_NEARLINK_PEER_MAC权限，则返回真实设备地址。否则，返回随机的设备地址 |
| [getState](arkts-connectivity-manager-getstate-f.md) | 获取星闪状态。 |
| [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) | 检查当前设备是否支持星闪。 |
| [offStateChange](arkts-connectivity-manager-offstatechange-f.md) | 取消订阅状态变更事件。 |
| [onStateChange](arkts-connectivity-manager-onstatechange-f.md) | 订阅状态变更事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disable](arkts-connectivity-manager-disable-f-sys.md) | 关闭星闪。 |
| [enable](arkts-connectivity-manager-enable-f-sys.md) | 开启星闪。 |
| [factoryReset](arkts-connectivity-manager-factoryreset-f-sys.md) | 恢复星闪设置。 |
| [getLocalAddress](arkts-connectivity-manager-getlocaladdress-f-sys.md) | 获取本端设备的MAC地址。 |
| [setConnectionMode](arkts-connectivity-manager-setconnectionmode-f-sys.md) | 设置设备的NearLink连接模式。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | 星闪状态的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | 连接模式的枚举。 |
<!--DelEnd-->

