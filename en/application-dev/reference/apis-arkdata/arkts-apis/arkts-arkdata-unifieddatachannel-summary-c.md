# Summary

```TypeScript
class Summary
```

Summarizes the data information of the **unifiedData** object, including the data type and size.

**Since:** 10

<!--Device-unifiedDataChannel-class Summary--><!--Device-unifiedDataChannel-class Summary-End-->

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

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-Summary-get filenameExtensions(): Array<string>--><!--Device-Summary-get filenameExtensions(): Array<string>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## overview

```TypeScript
get overview(): Record<string, number>
```

Indicates the overview information of unifiedData.

**Type:** Record&lt;string, number&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-Summary-get overview(): Record<string, long>--><!--Device-Summary-get overview(): Record<string, long>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## summary

```TypeScript
get summary(): Record<string, number>
```

A map for each type and data size, key is data type, value is the corresponding data size

**Type:** Record&lt;string, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Summary-get summary(): Record<string, long>--><!--Device-Summary-get summary(): Record<string, long>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set summary(value: Record<string, number>)
```

A map for each type and data size, key is data type, value is the corresponding data size

**Type:** Record&lt;string, number&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Summary-set summary(value: Record<string, long>)--><!--Device-Summary-set summary(value: Record<string, long>)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## totalSize

```TypeScript
get totalSize(): number
```

Total data size of data in Bytes

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Summary-get totalSize(): long--><!--Device-Summary-get totalSize(): long-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set totalSize(value: number)
```

Total data size of data in Bytes

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Summary-set totalSize(value: long)--><!--Device-Summary-set totalSize(value: long)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
