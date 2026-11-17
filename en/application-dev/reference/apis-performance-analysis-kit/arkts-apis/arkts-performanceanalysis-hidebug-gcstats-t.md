# GcStats

```TypeScript
type GcStats = Record<string, number>
```

Describes the key-value pair used to store GC statistics. This type does not support multi-thread operations. If this type is operated by multiple threads at the same time in an application, use a lock for it. It contains the following key-value information: <br>**"ark.gc.gc-count"**: number of GC times of the current thread. <br>**"ark.gc.gc-time"**: total GC duration triggered by the current thread, in milliseconds. <br>**"ark.gc.gc-bytes-allocated"**: size of the Ark VM memory allocated to the current thread, in bytes. <br>**"ark.gc.gc-bytes-freed"**: memory freed by GC of the current thread, in bytes. <br>**"ark.gc.fullgc-longtime-count"**: number of longtime full GC times triggered by the current thread.

**Type:** Record&lt;string, number&gt;

**Since:** 12

<!--Device-hidebug-type GcStats = Record<string, long>--><!--Device-hidebug-type GcStats = Record<string, long>-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
