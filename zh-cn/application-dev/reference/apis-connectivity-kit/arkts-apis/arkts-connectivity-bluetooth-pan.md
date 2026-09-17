# @ohos.bluetooth.pan(蓝牙pan模块)

本模块提供基于蓝牙个人局域网协议（Personal Area Networking，PAN）的蓝牙共享网络能力，支持本端作为NAP设备和PANU设备查询PAN支持状态、网络共享状态及获取连接状态等，适用于需要通过蓝牙实现个人局域网共享网络的场景。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { pan } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createPanProfile](arkts-connectivity-pan-createpanprofile-f.md) | 创建蓝牙PAN实例。通过该实例可使用本端作为NAP设备和PANU设备的接口，如：获取和其他设备间的蓝牙个人局域网服务连接状态。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PanProfile](arkts-connectivity-pan-panprofile-i.md) | 表示蓝牙PAN通信的实例，提供查询本端PAN支持状态、网络共享状态等能力，适用于蓝牙个人局域网共享网络场景。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PanProfile](arkts-connectivity-pan-panprofile-i-sys.md) | 表示蓝牙PAN通信的实例，提供查询本端PAN支持状态、网络共享状态等能力，适用于蓝牙个人局域网共享网络场景。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [BaseProfile](arkts-connectivity-pan-baseprofile-t.md) | 基础Profile接口定义，提供订阅和获取连接状态等公共能力。 |
