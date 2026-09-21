# @ohos.bluetooth.baseProfile(蓝牙baseProfile模块)

本模块提供不同的蓝牙技术协议的基础公共方法，为A2DP、HFP、PAN等蓝牙Profile提供连接状态查询、连接状态订阅与取消订阅等公共能力，适用于需要在应用中统一管理多种蓝牙Profile连接状态的场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { baseProfile } from '@kit.ConnectivityKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-baseprofile-baseprofile-i.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。如：[A2dpSourceProfile](arkts-connectivity-a2dp-a2dpsourceprofile-i.md)、[HandsFreeAudioGatewayProfile](arkts-connectivity-hfp-handsfreeaudiogatewayprofile-i-sys.md)等Profile类型都继承于该类。 |
| [StateChangeParam](arkts-connectivity-baseprofile-statechangeparam-i.md) | 本端和对端蓝牙设备间Profile连接状态变化参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-baseprofile-baseprofile-i-sys.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。如：[A2dpSourceProfile](arkts-connectivity-a2dp-a2dpsourceprofile-i.md)、[HandsFreeAudioGatewayProfile](arkts-connectivity-hfp-handsfreeaudiogatewayprofile-i-sys.md)等Profile类型都继承于该类。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DisconnectCause](arkts-connectivity-baseprofile-disconnectcause-e.md) | 枚举，Profile断开连接的原因。 |
| [PanRole](arkts-connectivity-baseprofile-panrole-e.md) | 枚举，PAN的不同角色。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionStrategy](arkts-connectivity-baseprofile-connectionstrategy-e-sys.md) | 枚举，表示Profile的连接策略。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-baseprofile-profileconnectionstate-t.md) | 本端和对端蓝牙设备间的Profile连接状态。 |
