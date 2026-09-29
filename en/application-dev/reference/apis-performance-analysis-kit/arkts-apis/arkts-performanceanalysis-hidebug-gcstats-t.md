# GcStats

```TypeScript
type GcStats = Record<string, number>
```

Describes the key-value pair used to store GC statistics. This type does not support multi-thread operations. If this type is operated by multiple threads at the same time in an application, use a lock for it.

**Since:** 12

<!--Device-hidebug-type GcStats = Record<string, long>--><!--Device-hidebug-type GcStats = Record<string, long>-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Type:** Record&lt;string, number&gt;
