# ErrorEvent

Provides detailed information about the exception that occurs during worker execution. The ErrorEvent class inherits from Event.

**Inheritance/Implementation:** ErrorEvent extends [Event](arkts-arkts-worker-event-i.md)

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## colno

```TypeScript
readonly colno: number
```

Serial number of the column where the exception is located.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## error

```TypeScript
readonly error: Object
```

Type of the exception.

**Type:** Object

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## filename

```TypeScript
readonly filename: string
```

File where the exception is located.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## lineno

```TypeScript
readonly lineno: number
```

Serial number of the line where the exception is located.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## message

```TypeScript
readonly message: string
```

Information about the exception.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
