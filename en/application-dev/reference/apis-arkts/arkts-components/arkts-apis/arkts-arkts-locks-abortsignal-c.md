# AbortSignal

Object used to abort an async operation. An instance of this class must be accessed in the same thread where the instance is created. Access to fields of this class from another thread is undefined behaviour.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## aborted

```TypeScript
aborted: boolean
```

Set to true to abort an operation.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## reason

```TypeScript
reason: T
```

Reason for the abort. This value will be used to reject the promise returned from lockAsync.

**Type:** T

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
