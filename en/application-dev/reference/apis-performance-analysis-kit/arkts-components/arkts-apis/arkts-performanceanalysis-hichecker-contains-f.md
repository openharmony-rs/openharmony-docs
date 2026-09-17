# contains

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## contains

```TypeScript
function contains(rule: bigint): boolean
```

Checks whether the specified rule exists in the collection of added rules. If the rule is of the thread level, this operation is performed only on the current thread.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md)

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to be checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. If the rule exists in the collection of added rules, **true** is returned; otherwise, **false** is returned. |

**Examples**

```TypeScript
// Add a rule.
hichecker.addRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

// Check whether the added rule exists in the collection of added rules.
hichecker.contains(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
hichecker.contains(hichecker.RULE_CAUTION_PRINT_LOG); // return false;
```
