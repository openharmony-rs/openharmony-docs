# addRule

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## addRule

```TypeScript
function addRule(rule: bigint): void
```

Adds one or more rules. HiChecker detects unexpected operations or gives feedback based on the added rules.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md)

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to be added. |

**Examples**

```TypeScript
// Add a rule.
hichecker.addRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Add multiple rules.
hichecker.addRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```
