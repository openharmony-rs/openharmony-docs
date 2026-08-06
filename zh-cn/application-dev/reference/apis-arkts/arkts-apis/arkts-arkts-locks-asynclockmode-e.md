# AsyncLockMode

锁操作对应的模式枚举。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-locks-enum AsyncLockMode--><!--Device-locks-enum AsyncLockMode-End-->

**系统能力：** SystemCapability.Utils.Lang

## SHARED

```TypeScript
SHARED = 1
```

共享锁模式。如果指定了此模式，允许​​多个线程或并发任务同时获取锁并执行操作。多用于读操作、无数据竞争的并行任务。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockMode-SHARED = 1--><!--Device-AsyncLockMode-SHARED = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## EXCLUSIVE

```TypeScript
EXCLUSIVE = 2
```

独占锁模式。如果指定了此模式，仅允许持有锁的任务执行。它与任何其他锁均不兼容​​，包括其他独占锁和共享锁。多用于写操作、数据更新、状态修改等可能产生竞争的场景。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockMode-EXCLUSIVE = 2--><!--Device-AsyncLockMode-EXCLUSIVE = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

