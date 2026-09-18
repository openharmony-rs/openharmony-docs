# isConcurrent

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## isConcurrent

```TypeScript
function isConcurrent(func: Function): boolean
```

Checks whether a function is a concurrent function.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | Function | Yes | Function to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the function is a concurrent function, that is, a function decorated with [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator); otherwise, **false** is returned. |

**Examples**

```TypeScript
@Concurrent
function test() {}

let result: Boolean = taskpool.isConcurrent(test);
console.info("result is: " + result);
```
