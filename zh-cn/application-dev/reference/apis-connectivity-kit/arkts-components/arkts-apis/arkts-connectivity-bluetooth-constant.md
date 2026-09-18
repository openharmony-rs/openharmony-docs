# @ohos.bluetooth.constant(蓝牙constant模块)

本模块提供了蓝牙Profile、设备类型相关的常量定义。开发者可使用这些常量进行蓝牙Profile连接状态判断、设备类型识别等操作，适用于蓝牙设备配对、连接管理、设备分类筛选等场景，便于在应用中统一引用标准协议与设备类型的常量值，提升代码可读性与可维护性。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { constant } from '@kit.ConnectivityKit';
```

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MajorClass](arkts-connectivity-constant-majorclass-e.md) | 枚举，蓝牙设备的主要类型。蓝牙标准协议字段。 |
| [MajorMinorClass](arkts-connectivity-constant-majorminorclass-e.md) | 枚举，蓝牙设备的子类型，在[MajorClass](arkts-connectivity-constant-majorclass-e.md)基础上进一步细分的类型。蓝牙标准协议字段。 |
| [ProfileConnectionState](arkts-connectivity-constant-profileconnectionstate-e.md) | 枚举，本端和对端蓝牙设备间的Profile连接状态。 |
| [ProfileId](arkts-connectivity-constant-profileid-e.md) | 枚举，表示蓝牙Profile协议的标识。 |
| [ProfileUuids](arkts-connectivity-constant-profileuuids-e.md) | 枚举，由蓝牙技术联盟（Bluetooth Special Interest Group）定义，使用通用唯一标识（Universally Unique Identifier，UUID）表示不同的蓝牙协议Profile。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessAuthorization](arkts-connectivity-constant-accessauthorization-e-sys.md) | 枚举，蓝牙访问授权状态。表示对端蓝牙设备访问本端蓝牙Profile（如电话簿、消息等）的授权状态，用于蓝牙数据访问授权场景。 |
<!--DelEnd-->
