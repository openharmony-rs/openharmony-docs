# AsyncLockMode

```TypeScript
enum AsyncLockMode
```

Mode of lock operations.

**Since:** 12

<!--Device-locks-enum AsyncLockMode--><!--Device-locks-enum AsyncLockMode-End-->

**System capability:** SystemCapability.Utils.Lang

## SHARED

```TypeScript
SHARED = 1
```

Shared lock operation. The operation could reenter if this mode is specified.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AsyncLockMode-SHARED = 1--><!--Device-AsyncLockMode-SHARED = 1-End-->

**System capability:** SystemCapability.Utils.Lang

## EXCLUSIVE

```TypeScript
EXCLUSIVE = 2
```

Exclusive lock operation. If this mode is specified, the operation is executed only when the lock is acquired exclusively.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AsyncLockMode-EXCLUSIVE = 2--><!--Device-AsyncLockMode-EXCLUSIVE = 2-End-->

**System capability:** SystemCapability.Utils.Lang
