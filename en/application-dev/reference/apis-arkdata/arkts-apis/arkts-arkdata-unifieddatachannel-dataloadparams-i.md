# DataLoadParams

```TypeScript
interface DataLoadParams
```

Describes the data loading policy of the sender in delayed loading scenarios.

When both loadHandler and delayedDataLoadHandler are passed in, delayedDataLoadHandler takes precedence and loadHandler does not take effect.

**Since:** 20

<!--Device-unifiedDataChannel-interface DataLoadParams--><!--Device-unifiedDataChannel-interface DataLoadParams-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## delayedDataLoadHandler

```TypeScript
delayedDataLoadHandler?: DelayedDataLoadHandler
```

Asynchronous handler used to load data in a delayed manner. The default value is undefined. If this parameter is not set, only loadHandler is used.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-DataLoadParams-delayedDataLoadHandler?: DelayedDataLoadHandler--><!--Device-DataLoadParams-delayedDataLoadHandler?: DelayedDataLoadHandler-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## loadHandler

```TypeScript
loadHandler: DataLoadHandler
```

Handler used to load data in a delayed manner. This handler is a synchronous function and is suitable for processing simple service logic. If the function involves complex service logic and takes a long time to execute (more than 3s), you are advised to use [DelayedDataLoadHandler](arkts-arkdata-unifieddatachannel-delayeddataloadhandler-t.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataLoadParams-loadHandler: DataLoadHandler--><!--Device-DataLoadParams-loadHandler: DataLoadHandler-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## dataLoadInfo

```TypeScript
dataLoadInfo: DataLoadInfo
```

Describes the data types and quantities that the current sender can generate.

**Type:** [DataLoadInfo](arkts-arkdata-unifieddatachannel-dataloadinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataLoadParams-dataLoadInfo: DataLoadInfo--><!--Device-DataLoadParams-dataLoadInfo: DataLoadInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
