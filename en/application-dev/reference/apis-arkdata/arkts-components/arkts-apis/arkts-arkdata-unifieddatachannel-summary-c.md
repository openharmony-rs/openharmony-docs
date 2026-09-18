# Summary

Summarizes the data information of the **unifiedData** object, including the data type and size.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## filenameExtensions

```TypeScript
get filenameExtensions(): Array<string>
```

File name extensions of file records in the unified data.

The extensions are unique, include the leading period, and use lowercase ASCII letters. For example, the file name extension of **myphoto.png** is **.png**. If no valid file name extension is available, an empty array is returned.

**Type:** Array&lt;string&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## overview

```TypeScript
get overview(): Record<string, number>
```

Indicates the overview information of unifiedData.

**Type:** Record&lt;string, number&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## summary

```TypeScript
get summary(): Record<string, number>
```

A map for each type and data size, key is data type, value is the corresponding data size

**Type:** Record&lt;string, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set summary(value: Record<string, number>)
```

A map for each type and data size, key is data type, value is the corresponding data size

**Type:** Record&lt;string, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## totalSize

```TypeScript
get totalSize(): number
```

Total data size of data in Bytes

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set totalSize(value: number)
```

Total data size of data in Bytes

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
