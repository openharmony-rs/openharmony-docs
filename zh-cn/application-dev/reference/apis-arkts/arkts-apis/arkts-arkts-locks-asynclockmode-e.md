# AsyncLockMode

锁操作对应的模式枚举。

**起始版本：** 12

<!--Device-locks-enum AsyncLockMode--><!--Device-locks-enum AsyncLockMode-End-->

**系统能力：** SystemCapability.Utils.Lang

## SHARED

```TypeScript
SHARED = 1
```

共享锁操作。如果指定了此模式，允许操作重入。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockMode-SHARED = 1--><!--Device-AsyncLockMode-SHARED = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## EXCLUSIVE

```TypeScript
EXCLUSIVE = 2
```

独占锁操作。如果指定了此模式，只有在独占获取锁时才执行操作。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncLockMode-EXCLUSIVE = 2--><!--Device-AsyncLockMode-EXCLUSIVE = 2-End-->

**系统能力：** SystemCapability.Utils.Lang

