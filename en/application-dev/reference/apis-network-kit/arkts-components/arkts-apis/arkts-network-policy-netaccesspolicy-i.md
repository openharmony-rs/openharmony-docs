# NetAccessPolicy

```TypeScript
export interface NetAccessPolicy
```

Defines the network access policy information.

**Since:** 26.0.0

<!--Device-policy-export interface NetAccessPolicy--><!--Device-policy-export interface NetAccessPolicy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## allowCellular

```TypeScript
allowCellular: boolean
```

Whether to allow Internet access over the cellular network.

**true**: yes.

**false**: no.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NetAccessPolicy-allowCellular: boolean--><!--Device-NetAccessPolicy-allowCellular: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## allowWiFi

```TypeScript
allowWiFi: boolean
```

Whether to allow Internet access over Wi-Fi.

**true**: yes;

**false**: no.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NetAccessPolicy-allowWiFi: boolean--><!--Device-NetAccessPolicy-allowWiFi: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
