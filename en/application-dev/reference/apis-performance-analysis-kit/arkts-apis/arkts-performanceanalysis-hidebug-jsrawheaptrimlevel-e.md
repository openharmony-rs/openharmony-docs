# JsRawHeapTrimLevel

Enumerates the trimming levels of the heap snapshot.

**TRIM_LEVEL_2** takes a longer time than **TRIM_LEVEL_1**. The threshold for screen freezing is 6 seconds. With **TRIM_LEVEL_1**, the trim duration stays below this threshold. Upon switching to **TRIM_LEVEL_2**, the duration may exceed 6s, triggering an **APP_FREEZE** (screen freeze event) and causing the system to kill the application; the trim level then reverts to **TRIM_LEVEL_1**.

You are advised to use **TRIM_LEVEL_1** to ensure application stability and use **TRIM_LEVEL_2 **only when more complete trimming is required.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## TRIM_LEVEL_1

```TypeScript
TRIM_LEVEL_1 = 0
```

Level 1 trimming, mainly used for strings.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## TRIM_LEVEL_2

```TypeScript
TRIM_LEVEL_2 = 1
```

Level 2 trimming, which reduces the size of the object address identifier from 8 bytes to 4 bytes based on **TRIM_LEVEL_1**.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
