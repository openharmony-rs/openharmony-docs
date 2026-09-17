# AsyncLockInfo

Information about a lock.

**Since:** 12

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

**System capability:** SystemCapability.Utils.Lang

## mode

```TypeScript
mode: AsyncLockMode
```

Lock operation mode.

**Type:** [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

Name of the lock.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
