# DataLoadParams

Defines the data loading policy for the data sender in the lazy loading scenario.

If both **loadHandler** and **delayedDataLoadHandler** are passed, **delayedDataLoadHandler** is preferentially used, and **loadHandler** does not take effect.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## delayedDataLoadHandler

```TypeScript
delayedDataLoadHandler?: DelayedDataLoadHandler
```

Indicates the callback function for deferred and non-blocking data loading. This handler is optional. If it is provided, it will take precedence over the synchronous DataLoadHandler (i.e., DataLoadHandler will be ignored).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## loadHandler

```TypeScript
loadHandler: DataLoadHandler
```

Indicates the callback function for loading data.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## dataLoadInfo

```TypeScript
dataLoadInfo: DataLoadInfo
```

Indicates data loading information.

**Type:** [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
