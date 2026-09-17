# removeRule

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## removeRule

```TypeScript
function removeRule(rule: bigint): void
```

Removes one or more rules. The removed rules will become ineffective.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md)

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to be removed. |

**Examples**

```TypeScript
// Remove a rule.
hichecker.removeRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Remove multiple rules.
hichecker.removeRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```
