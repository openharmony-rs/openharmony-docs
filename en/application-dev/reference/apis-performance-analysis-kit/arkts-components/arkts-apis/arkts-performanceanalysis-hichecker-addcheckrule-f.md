# addCheckRule

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## addCheckRule

```TypeScript
function addCheckRule(rule: bigint) : void
```

Adds one or more check rules. HiChecker detects unexpected operations or gives feedback based on the added rules. You can use **grep HiChecker** to check for the application running information in the hilog.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | the parameter check failed, only one bigint type parameter is needed |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // Add a rule.
    hichecker.addCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);
    // Add multiple rules.
    // hichecker.addCheckRule(
    //     hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```
