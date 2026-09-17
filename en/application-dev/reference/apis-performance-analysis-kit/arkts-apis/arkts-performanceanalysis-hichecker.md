# @ohos.hichecker

The HiChecker module allows you to check issues that may be easily ignored during development of applications (including system-built and third-party applications). Such issues include calling of time-consuming functions by key application threads, event distribution and execution timeout in application processes, and ability resource leakage in application processes. The issues are recorded in logs or lead to process crashes explicitly so that you can find and rectify them.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiChecker

## Modules to Import

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md) | Adds one or more check rules. HiChecker detects unexpected operations or gives feedback based on the added rules. You can use **grep HiChecker** to check for the application running information in the hilog. |
| [addRule](arkts-performanceanalysis-hichecker-addrule-f.md) | Adds one or more rules. HiChecker detects unexpected operations or gives feedback based on the added rules. |
| [contains](arkts-performanceanalysis-hichecker-contains-f.md) | Checks whether the specified rule exists in the collection of added rules. If the rule is of the thread level, this operation is performed only on the current thread. |
| [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md) | Checks whether the specified rule exists in the collection of added rules. If the rule is of the thread level, this operation is performed only on the current thread. |
| [getRule](arkts-performanceanalysis-hichecker-getrule-f.md) | Obtains a collection of thread, process, and alarm rules that have been added. |
| [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md) | Removes one or more rules. The removed rules will become ineffective. |
| [removeRule](arkts-performanceanalysis-hichecker-removerule-f.md) | Removes one or more rules. The removed rules will become ineffective. |

### Constants

| Name | Description |
| --- | --- |
| [RULE_CAUTION_PRINT_LOG](arkts-performanceanalysis-hichecker-con.md#rule_caution_print_log) | Alarm rule, which is programmed to print a log when an alarm is generated. |
| [RULE_CAUTION_TRIGGER_CRASH](arkts-performanceanalysis-hichecker-con.md#rule_caution_trigger_crash) | Alarm rule, which is programmed to force the application to exit when an alarm is generated. |
| [RULE_CHECK_ABILITY_CONNECTION_LEAK](arkts-performanceanalysis-hichecker-con.md#rule_check_ability_connection_leak) | Caution rule, which is programmed to detect whether ability leakage has occurred. |
| [RULE_CHECK_ARKUI_PERFORMANCE](arkts-performanceanalysis-hichecker-con.md#rule_check_arkui_performance) | Caution rule, which is programmed to detect the ArkUI performance. |
| [RULE_THREAD_CHECK_NETWORK_USAGE](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_network_usage) | Caution rule, which is programmed to detect whether the thread invokes a time-consuming network API. |
| [RULE_THREAD_CHECK_SLOW_PROCESS](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_slow_process) | Caution rule, which is programmed to detect whether any time-consuming function is invoked. |
