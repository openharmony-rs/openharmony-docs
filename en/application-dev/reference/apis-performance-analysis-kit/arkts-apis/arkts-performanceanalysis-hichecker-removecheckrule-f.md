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

If the rule level of the passed-in rule is thread level, the rule is removed only from the current thread.

**Since:** 9

<!--Device-hichecker-function removeCheckRule(rule: bigint) : void--><!--Device-hichecker-function removeCheckRule(rule: bigint) : void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | bigint | Yes | Rule to remove. Multiple rules can be combined using the OR operation. Available values include:<br>**RULE_CAUTION_PRINT_LOG** (log recording), **RULE_CAUTION_TRIGGER_CRASH** (application exit), and **RULE_THREAD_CHECK_SLOW_PROCESS** (detect time-consuming function calls). For details, see the constants. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

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
