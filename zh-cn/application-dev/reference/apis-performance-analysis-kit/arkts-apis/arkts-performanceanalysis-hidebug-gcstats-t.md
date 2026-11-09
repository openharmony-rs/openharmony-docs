# GcStats

```TypeScript
type GcStats = Record<string, number>
```

描述用于存储GC统计信息的键值对。该类型不支持多线程操作，如果应用中存在多线程同时访问，需加锁保护。包含以下键值信息：<br>"ark.gc.gc-count"：当前线程的GC次数。<br>"ark.gc.gc-time"：当前线程触发的GC总耗时，以ms为单位。<br>"ark.gc.gc-bytes-allocated"：当前线程Ark虚拟机已分配的内存大小，以B为单位。<br>"ark.gc.gc-bytes-freed"：当前线程GC成功回收的内存，以B为单位。<br>"ark.gc.fullgc-longtime-count"：当前线程超长fullGC次数。

**类型：** Record&lt;string, number&gt;

**起始版本：** 12

<!--Device-hidebug-type GcStats = Record<string, long>--><!--Device-hidebug-type GcStats = Record<string, long>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
