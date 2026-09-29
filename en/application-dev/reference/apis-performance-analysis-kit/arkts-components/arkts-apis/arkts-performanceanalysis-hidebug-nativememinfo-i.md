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

The size of the private clean memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-privateClean: bigint--><!--Device-NativeMemInfo-privateClean: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## privateDirty

```TypeScript
privateDirty: bigint
```

The size of the private dirty memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-privateDirty: bigint--><!--Device-NativeMemInfo-privateDirty: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## pss

```TypeScript
pss: bigint
```

Process proportional set size memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-pss: bigint--><!--Device-NativeMemInfo-pss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

Resident set size, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-rss: bigint--><!--Device-NativeMemInfo-rss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedClean

```TypeScript
sharedClean: bigint
```

The size of the shared clean memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-sharedClean: bigint--><!--Device-NativeMemInfo-sharedClean: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedDirty

```TypeScript
sharedDirty: bigint
```

The size of the shared dirty memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-sharedDirty: bigint--><!--Device-NativeMemInfo-sharedDirty: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vss

```TypeScript
vss: bigint
```

Virtual set size memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-NativeMemInfo-vss: bigint--><!--Device-NativeMemInfo-vss: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
