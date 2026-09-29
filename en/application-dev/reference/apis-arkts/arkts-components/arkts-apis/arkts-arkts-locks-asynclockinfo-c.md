# AsyncLockInfo

```TypeScript
class AsyncLockInfo
```

Information about a lock.

**Since:** 12

<!--Device-locks-class AsyncLockInfo--><!--Device-locks-class AsyncLockInfo-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## contextId

```TypeScript
contextId: number
```

lockAsync caller's execution context identifier.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AsyncLockInfo-contextId: number--><!--Device-AsyncLockInfo-contextId: number-End-->

**System capability:** SystemCapability.Utils.Lang

## mode

```TypeScript
mode: AsyncLockMode
```

Lock operation mode.

**Type:** [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AsyncLockInfo-mode: AsyncLockMode--><!--Device-AsyncLockInfo-mode: AsyncLockMode-End-->

**System capability:** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

Name of the lock.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AsyncLockInfo-name: string--><!--Device-AsyncLockInfo-name: string-End-->

**System capability:** SystemCapability.Utils.Lang
