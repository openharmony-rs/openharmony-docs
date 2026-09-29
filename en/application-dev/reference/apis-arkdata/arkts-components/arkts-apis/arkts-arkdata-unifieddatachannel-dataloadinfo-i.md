# DataLoadInfo

```TypeScript
interface DataLoadInfo
```

Defines type and quantity of the data to load.

- Used by the **data sender** to define the data range that can be provided. This field is mandatory.  
- Used by the **data receiver** to define the expected data type and quantity. This field is optional.

**Since:** 20

<!--Device-unifiedDataChannel-interface DataLoadInfo--><!--Device-unifiedDataChannel-interface DataLoadInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## recordCount

```TypeScript
recordCount?: number
```

Indicates the maximum number of data records to be loaded.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-DataLoadInfo-recordCount?: long--><!--Device-DataLoadInfo-recordCount?: long-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## types

```TypeScript
types?: Set<string>
```

Represents the data type or supported types to load. <br>This parameter is mandatory when used by the data provider.

**Type:** Set&lt;string&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-DataLoadInfo-types?: Set<string>--><!--Device-DataLoadInfo-types?: Set<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
