# NativeMemInfo

```TypeScript
interface NativeMemInfo
```

Describes memory information of the application process.

**Since:** 12

<!--Device-hidebug-interface NativeMemInfo--><!--Device-hidebug-interface NativeMemInfo-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## privateClean

```TypeScript
privateClean: bigint
```

Size of the private clean memory, in KB. The value of this parameter is obtained by reading the value of **Private_Clean** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-privateClean: bigint--><!--Device-NativeMemInfo-privateClean: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## privateDirty

```TypeScript
privateDirty: bigint
```

Size of the private dirty memory, in KB. The value of this parameter is obtained by reading the value of **Private_Dirty** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-privateDirty: bigint--><!--Device-NativeMemInfo-privateDirty: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## pss

```TypeScript
pss: bigint
```

Size of the occupied physical memory (including the proportionally allocated memory occupied by the shared library), in KB. The value of this parameter is obtained by summing up the values of **Pss** and **SwapPss** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-pss: bigint--><!--Device-NativeMemInfo-pss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

Size of the occupied physical memory (including the memory occupied by the shared library), in KB. The value of this parameter is obtained by reading the value of **Rss** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-rss: bigint--><!--Device-NativeMemInfo-rss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedClean

```TypeScript
sharedClean: bigint
```

Size of the shared clean memory, in KB. The value of this parameter is obtained by reading the value of **Shared_Clean** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-sharedClean: bigint--><!--Device-NativeMemInfo-sharedClean: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedDirty

```TypeScript
sharedDirty: bigint
```

Size of the shared dirty memory, in KB. The value of this parameter is obtained by reading the value of **Shared_Dirty** in the **\/proc/{pid}/smaps_rollup** node.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-sharedDirty: bigint--><!--Device-NativeMemInfo-sharedDirty: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vss

```TypeScript
vss: bigint
```

Size of the occupied virtual memory (including the memory occupied by the shared library), in KB. The value of this parameter is obtained by multiplying the value of **size** in the **\/proc/{pid}/statm** node by **4**.

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-vss: bigint--><!--Device-NativeMemInfo-vss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
