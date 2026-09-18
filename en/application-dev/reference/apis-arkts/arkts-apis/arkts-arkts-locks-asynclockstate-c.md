# AsyncLockState

Information about all lock operations on the AsyncLock instance.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## held

```TypeScript
held: AsyncLockInfo[]
```

Held locks information.

**Type:** [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md)[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## pending

```TypeScript
pending: AsyncLockInfo[]
```

Pending locks information.

**Type:** [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md)[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
