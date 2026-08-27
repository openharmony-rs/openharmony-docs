# GcStats

```TypeScript
type GcStats = Record<string, number>
```

描述用于存储GC统计信息的键值对。该类型不支持多线程操作，如果应用中存在多线程同时访问，需加锁保护。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**属性类型：** Record&lt;string, number&gt;
