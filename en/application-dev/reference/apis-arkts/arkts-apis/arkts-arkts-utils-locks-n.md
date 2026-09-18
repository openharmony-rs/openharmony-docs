# locks(Defines the utils for ArkTS)

Asynchronous lock.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AsyncLock](arkts-arkts-locks-asynclock-c.md) | Class to execute an asynchronous operation under lock. |
| [AsyncLockOptions](arkts-arkts-locks-asynclockoptions-c.md) | Lock operation's options |
| [AsyncLockState](arkts-arkts-locks-asynclockstate-c.md) | Information about all lock operations on the AsyncLock instance. |
| [AsyncLockInfo](arkts-arkts-locks-asynclockinfo-c.md) | Information about a lock. |
| [AbortSignal](arkts-arkts-locks-abortsignal-c.md) | Object used to abort an async operation. An instance of this class must be accessed in the same thread where the instance is created. Access to fields of this class from another thread is undefined behaviour. |
| [ConditionVariable](arkts-arkts-locks-conditionvariable-c.md) | Object used for thread synchronization. |

### Types

| Name | Description |
| --- | --- |
| [AsyncLockCallback](arkts-arkts-locks-asynclockcallback-t.md) | Type of callback for asyncLock operation. |

### Enums

| Name | Description |
| --- | --- |
| [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md) | Mode of lock operations. |
