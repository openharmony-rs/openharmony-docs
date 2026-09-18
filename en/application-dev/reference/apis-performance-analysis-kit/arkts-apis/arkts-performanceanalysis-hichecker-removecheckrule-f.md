# removeCheckRule

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## removeCheckRule

```TypeScript
function removeCheckRule(rule: bigint) : void
```

Removes one or more rules. The removed rules will become ineffective.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | the parameter check failed, only one bigint type parameter is needed |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // Remove a rule.
    hichecker.removeCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);
    // Remove multiple rules.
    // hichecker.removeCheckRule(
    //     hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```
