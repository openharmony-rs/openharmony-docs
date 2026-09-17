# ConditionVariable

Object used for thread synchronization.

**Since:** 18

**Decorator:** @Sendable

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

Default constructor.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## notifyAll

```TypeScript
notifyAll(): void
```

Notify all waiting promise.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## notifyOne

```TypeScript
notifyOne(): void
```

Notify one waiting promise.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## request

```TypeScript
static request(name: string): ConditionVariable
```

Find or create an instance of ConditionVariable using the specified name.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the ConditionVariable to find or create. |

**Return value:**

| Type | Description |
| --- | --- |
| [ConditionVariable](arkts-arkts-locks-conditionvariable-c.md) | Returns an instance of ConditionVariable. |

## wait

```TypeScript
wait(): Promise<void>
```

Waits for the ConditionVariable to be notified.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A promise will be resolved once the ConditionVariable is notified.. |

## waitFor

```TypeScript
waitFor(timeout: number): Promise<void>
```

Waits for the ConditionVariable to be notified, or until the specified time limit is reached.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | The maximum time to wait. The value should be an integer.<br>Unit: ms. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A promise that will be resolved once the ConditionVariable is notified or the specified time limit is reached. |
