# @ohos.nearlink.constant(星闪公共常量定义)

本模块提供了星闪通信中共用的一些常量定义，包括设备配对状态、设备连接状态、设备类型等枚举值。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { nearlinkConstant } from '@kit.ConnectivityKit';
```

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AcbState](arkts-connectivity-nearlinkconstant-acbstate-e.md) | 表示和远端设备的逻辑链路连接状态，为枚举值。 |
| [ConnectionState](arkts-connectivity-nearlinkconstant-connectionstate-e.md) | 表示和远端设备的连接状态，为枚举值。 |
| [DeviceClass](arkts-connectivity-nearlinkconstant-deviceclass-e.md) | 表示设备类型，为枚举值。 |
| [PairingState](arkts-connectivity-nearlinkconstant-pairingstate-e.md) | 表示和远端设备的配对状态，为枚举值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectionInterval](arkts-connectivity-nearlinkconstant-connectioninterval-e-sys.md) | 连接间隔的枚举值。间隔越小，时延越低、吞吐越高但功耗越大；间隔越大功耗越低但时延越高。高速档适用于高吞吐低时延场景，低速档适用于对功耗敏感场景。 |
<!--DelEnd-->
