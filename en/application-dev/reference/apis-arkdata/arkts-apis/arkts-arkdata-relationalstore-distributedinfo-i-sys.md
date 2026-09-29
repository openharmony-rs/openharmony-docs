# DistributedInfo (System API)

```TypeScript
interface DistributedInfo
```

Manages the distributed info of the table.

**Since:** 24

<!--Device-relationalStore-interface DistributedInfo--><!--Device-relationalStore-interface DistributedInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## flag

```TypeScript
flag?: DistributedOrigin
```

Specifies the data origin sources.

**Type:** [DistributedOrigin](arkts-arkdata-relationalstore-distributedorigin-e-sys.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedInfo-flag?: DistributedOrigin--><!--Device-DistributedInfo-flag?: DistributedOrigin-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## oriDevice

```TypeScript
oriDevice?: string
```

Specifies the data origin sources device ID.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistributedInfo-oriDevice?: string--><!--Device-DistributedInfo-oriDevice?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.
