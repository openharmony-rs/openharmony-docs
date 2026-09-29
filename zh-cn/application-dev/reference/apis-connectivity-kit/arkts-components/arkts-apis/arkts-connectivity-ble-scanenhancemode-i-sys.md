# ScanEnhanceMode（系统接口）

```TypeScript
interface ScanEnhanceMode
```

The enum of gatt characteristic write type

**起始版本：** 26.0.0

<!--Device-ble-interface ScanEnhanceMode--><!--Device-ble-interface ScanEnhanceMode-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## enhanceMode

```TypeScript
enhanceMode: EnhanceMode
```

扫描增强的模式。

**类型：** [EnhanceMode](arkts-connectivity-ble-enhancemode-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanEnhanceMode-enhanceMode: EnhanceMode--><!--Device-ScanEnhanceMode-enhanceMode: EnhanceMode-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## timeout

```TypeScript
timeout: number
```

扫描增强的持续时间。取值范围为全体整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScanEnhanceMode-timeout: int--><!--Device-ScanEnhanceMode-timeout: int-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
