# @ohos.bluetooth.map(蓝牙map模块)

本模块提供基于消息访问协议（Message Access Profile，MAP）的蓝牙消息访问能力，支持创建MSE实例、获取和订阅设备间蓝牙消息服务连接状态等，适用于需要通过蓝牙协议进行消息访问与连接管理的场景。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { map } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMapMseProfile](arkts-connectivity-map-createmapmseprofile-f.md) | 创建蓝牙消息访问协议中的MSE实例。通过该实例可使用本端作为MSE设备时提供的接口，如：获取和其他设备间的蓝牙消息服务连接状态。适用于蓝牙消息同步、车载蓝牙消息查看等场景。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MapMseProfile](arkts-connectivity-map-mapmseprofile-i-sys.md) | 该实例表示蓝牙消息访问协议中的MSE角色。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-map-baseprofile-t.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessAuthorization](arkts-connectivity-map-accessauthorization-t-sys.md) |  |
<!--DelEnd-->
