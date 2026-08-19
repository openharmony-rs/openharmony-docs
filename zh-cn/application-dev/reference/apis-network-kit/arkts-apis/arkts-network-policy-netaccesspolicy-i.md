# NetAccessPolicy

应用联网策略信息。

**起始版本：** 26.0.0

<!--Device-policy-export interface NetAccessPolicy--><!--Device-policy-export interface NetAccessPolicy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## allowCellular

```TypeScript
allowCellular: boolean
```

是否允许使用蜂窝网络上网。 true：允许使用蜂窝网络上网。 false： 不允许使用蜂窝网络上网。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetAccessPolicy-allowCellular: boolean--><!--Device-NetAccessPolicy-allowCellular: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## allowWiFi

```TypeScript
allowWiFi: boolean
```

是否允许使用Wi-Fi网络上网。 true：允许使用Wi-Fi网络上网。 false： 不允许使用Wi-Fi网络上网。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetAccessPolicy-allowWiFi: boolean--><!--Device-NetAccessPolicy-allowWiFi: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

