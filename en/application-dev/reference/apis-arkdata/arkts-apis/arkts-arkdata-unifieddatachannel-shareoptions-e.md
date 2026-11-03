# ShareOptions

```TypeScript
enum ShareOptions
```

Enumerates the usage scope types supported by UDMF within a device.

**Since:** 12

<!--Device-unifiedDataChannel-enum ShareOptions--><!--Device-unifiedDataChannel-enum ShareOptions-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CROSS_APP

```TypeScript
CROSS_APP = 1
```

Indicates that the data can be used across applications on this device.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ShareOptions-CROSS_APP = 1--><!--Device-ShareOptions-CROSS_APP = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## IN_APP

```TypeScript
IN_APP = 0
```

Indicates that the data can be used within the same application on this device.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ShareOptions-IN_APP = 0--><!--Device-ShareOptions-IN_APP = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
