# DataLoadInfo

```TypeScript
interface DataLoadInfo
```

Describes the type and quantity of the data to be loaded.

- Used on the **data sender** side to indicate the range of data that can actually be provided. This field must be  
set.  
- Used on the **data receiver** side to indicate the type and quantity of data expected to be loaded. This field  
can be set as needed.

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

Maximum number of data records expected or that can be provided. The default value is **0**, and the value range is [0, 2<sup>32</sup>-1]. If the value exceeds the range, the default value is used. If the value is a floating-point number, only the integer part is used. When used for drag-and-drop, this value is displayed as the badge count, with a maximum of 2<sup>31</sup>-1. If the value exceeds this maximum, the badge is not displayed. When used as the badge count, its priority is lower than that of the numberBadge method in [DragPreviewOptions](../../apis-arkui/arkts-components/arkts-arkui-common-comp-dragpreviewoptions-i.md)

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataLoadInfo-recordCount?: long--><!--Device-DataLoadInfo-recordCount?: long-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## types

```TypeScript
types?: Set<string>
```

Set of data types. The default value is an empty set.

**Type:** Set&lt;string&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataLoadInfo-types?: Set<string>--><!--Device-DataLoadInfo-types?: Set<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
