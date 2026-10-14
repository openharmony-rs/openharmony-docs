# @ohos.hichecker (HiChecker)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Lutao98-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=111816d7ef19f2d98b21b4e02b20c33665536af8 translatedAt=2026-09-16T11:16:21.146Z pushedAt=2026-09-20T09:01:52.277Z -->

HiChecker can be used as a detection tool in the application development phase to detect some easily overlooked issues during code running, such as time-consuming calls in application threads and Ability resource leakage in the application process. Developers can view specific issues through logs or process crashes and fix them to improve the application experience.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { hichecker } from '@kit.PerformanceAnalysisKit';
```


## Constants

Provides the constants of all rule types.

**System capability**: SystemCapability.HiviewDFX.HiChecker

| Name                                            | Type     | Value        | Description                                                  |
| ------------------------------------------------ | -------- | -----------| ------------------------------------------------------ |
| RULE_CAUTION_PRINT_LOG                           | bigint   | 1ULL << 63 | Alarm rule, which is programmed to print a log when an alarm is generated.                           |
| RULE_CAUTION_TRIGGER_CRASH                       | bigint   | 1ULL << 62 | Alarm rule, which is programmed to force the application to exit when an alarm is generated.                         |
| RULE_THREAD_CHECK_SLOW_PROCESS                   | bigint   | 1ULL       | Caution rule, which is programmed to detect whether any time-consuming function is invoked.                     |
| RULE_THREAD_CHECK_NETWORK_USAGE                  | bigint   | 1ULL << 1  | Caution rule, which is programmed to detect whether the thread invokes a time-consuming network API.<br>**Since:** 26.0.0 |
| RULE_CHECK_ABILITY_CONNECTION_LEAK               | bigint   | 1ULL << 33 | Detection Rule, checks whether an Ability leak occurs.                      |
| RULE_CHECK_ARKUI_PERFORMANCE<sup>11+</sup>       | bigint   | 1ULL << 34 | Caution rule, which is programmed to detect the ArkUI performance.                              |

## hichecker.addCheckRule<sup>9+</sup>

addCheckRule(rule: bigint): void

Adds one or more rules to the system. The system performs detection or gives feedback based on the added rules. When a corresponding rule is triggered, you can use **grep HiChecker** in hilog to view the running information.

If the rule level of the passed-in rule is thread level, the rule takes effect only in the current thread.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| **rule**   | bigint | Yes   | Rule to add. Multiple rules can be combined using the OR operation. Available values include: <br>**RULE_CAUTION_PRINT_LOG** (log recording), **RULE_CAUTION_TRIGGER_CRASH** (application exit), **RULE_THREAD_CHECK_SLOW_PROCESS** (detect time-consuming function calls), and so on. For details, see [Constants](#constants). |

**Error codes**

| ID | Error Message |
| ------- | ----------------------------------------------------------------- |
| 401 | the parameter check failed, only one bigint type parameter is needed  |

**Example**

```ts
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

## hichecker.removeCheckRule<sup>9+</sup>

removeCheckRule(rule: bigint): void

Removes one or more rules. The removed rules will no longer take effect.

If the rule level of the passed-in rule is thread level, the rule is removed only from the current thread.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| **rule** | bigint | Yes | Rule to be removed. Multiple rules can be combined using the OR operation. Available values include: <br>**RULE_CAUTION_PRINT_LOG** (log recording), **RULE_CAUTION_TRIGGER_CRASH** (application exit), **RULE_THREAD_CHECK_SLOW_PROCESS** (detect time-consuming function calls), etc. For details, see [Constants](#constants). |

**Error codes**

| ID | Error Message |
| ------- | ----------------------------------------------------------------- |
| 401 | the parameter check failed, only one bigint type parameter is needed  |

**Example**

```ts
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

## hichecker.containsCheckRule<sup>9+</sup>

containsCheckRule(rule: bigint): boolean

Checks whether the currently added rule set contains a specific rule.

If the rule level of the passed-in rule is thread level, the query is performed only in the current thread.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| rule   | bigint | Yes  | Rule to be checked.|

**Return value**

| Type   | Description                                                      |
| ------- | ---------------------------------------------------------- |
| boolean | Check result. If the rule exists in the collection of added rules, **true** is returned; otherwise, **false** is returned.|

**Error codes**

| ID | Error Message |
| ------- | ----------------------------------------------------------------- |
| 401 | the parameter check failed, only one bigint type parameter is needed  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // Add a rule.
    hichecker.addCheckRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

    // Check whether the added rule exists in the collection of added rules.
    hichecker.containsCheckRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
    hichecker.containsCheckRule(hichecker.RULE_CAUTION_PRINT_LOG); // return false;
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```

## hichecker.addRule<sup>(deprecated)</sup>

addRule(rule: bigint): void

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [hichecker.addCheckRule](#hicheckeraddcheckrule9) instead.

Adds one or more rules. HiChecker detects unexpected operations or gives feedback based on the added rules.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| rule   | bigint | Yes  | Rule to be added.|

**Example**

```ts
// Add a rule.
hichecker.addRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Add multiple rules.
hichecker.addRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```

## hichecker.removeRule<sup>(deprecated)</sup>

removeRule(rule: bigint): void

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [hichecker.removeCheckRule](#hicheckerremovecheckrule9) instead.

Removes one or more rules. The removed rules will become ineffective.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| rule   | bigint | Yes  | Rule to be removed.|

**Example**

```ts
// Remove a rule.
hichecker.removeRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Remove multiple rules.
hichecker.removeRule(
          hichecker.RULE_CAUTION_PRINT_LOG | hichecker.RULE_CAUTION_TRIGGER_CRASH);
```

## hichecker.getRule

getRule(): bigint 

Obtains a collection of thread, process, and alarm rules that have been added.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Return value**

| Type  | Description                  |
| ------ | ---------------------- |
| bigint | Collection of added rules.|

**Example**

```ts
// Add a rule.
hichecker.addCheckRule(hichecker.RULE_CAUTION_PRINT_LOG);

// Obtain the collection of added rules.
hichecker.getRule();
```

## hichecker.contains<sup>(deprecated)</sup>

contains(rule: bigint): boolean

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [hichecker.containsCheckRule](#hicheckercontainscheckrule9) instead.

Checks whether the specified rule exists in the collection of added rules. If the rule is of the thread level, this operation is performed only on the current thread.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type  | Mandatory| Description            |
| ------ | ------ | ---- | ---------------- |
| rule   | bigint | Yes  | Rule to be checked.|

**Return value**

| Type   | Description                                                      |
| ------- | ---------------------------------------------------------- |
| boolean | Check result. If the rule exists in the collection of added rules, **true** is returned; otherwise, **false** is returned.|

**Example**

```ts
// Add a rule.
hichecker.addRule(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS);

// Check whether the added rule exists in the collection of added rules.
hichecker.contains(hichecker.RULE_THREAD_CHECK_SLOW_PROCESS); // return true;
hichecker.contains(hichecker.RULE_CAUTION_PRINT_LOG); // return false;
```
