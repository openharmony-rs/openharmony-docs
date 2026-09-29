# State

```TypeScript
enum State
```

Enumerates the task states. After a task is created and **execute()** is called, the task is placed in the internal queue of the task pool and the state is **WAITING**. When the task is being executed by the worker thread of the task pool, the state changes to **RUNNING**. After the task is executed and the result is returned, the state is reset to **WAITING**. When the task is proactively canceled, the state changes to **CANCELED**.

**Since:** 10

<!--Device-taskpool-enum State--><!--Device-taskpool-enum State-End-->

**System capability:** SystemCapability.Utils.Lang

## WAITING

```TypeScript
WAITING = 1
```

The task is waiting.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-State-WAITING = 1--><!--Device-State-WAITING = 1-End-->

**System capability:** SystemCapability.Utils.Lang

## RUNNING

```TypeScript
RUNNING = 2
```

The task is running.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-State-RUNNING = 2--><!--Device-State-RUNNING = 2-End-->

**System capability:** SystemCapability.Utils.Lang

## CANCELED

```TypeScript
CANCELED = 3
```

The task is canceled.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-State-CANCELED = 3--><!--Device-State-CANCELED = 3-End-->

**System capability:** SystemCapability.Utils.Lang
