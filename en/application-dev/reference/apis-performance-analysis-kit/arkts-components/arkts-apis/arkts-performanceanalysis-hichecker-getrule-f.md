# getRule

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## getRule

```TypeScript
function getRule() : bigint
```

Obtains a collection of thread, process, and alarm rules that have been added.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Collection of added rules. |

**Examples**

```TypeScript
// Add a rule.
hichecker.addCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Obtain the collection of added rules.
hichecker.getRule(); // return 1n;
```
