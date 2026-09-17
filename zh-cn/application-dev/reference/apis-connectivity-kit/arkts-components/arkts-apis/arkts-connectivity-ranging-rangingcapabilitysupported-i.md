# RangingCapabilitySupported

描述设备支持的测距类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## nearlinkHadm

```TypeScript
nearlinkHadm: boolean
```

星闪HADM测距类型是否支持。值为true时可使用[startRanging](arkts-connectivity-ranging-startranging-f.md)或[startPassiveRanging](arkts-connectivity-ranging-startpassiveranging-f.md)发起测距。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
