# @ohos.hichecker

HiChecker可以作为应用开发阶段使用的检测工具，用于检测代码运行过程中部分易忽略的问题，如应用线程出现耗时调用、应用进程中Ability资源泄露等问题。开发者可以通过日志记录或进程crash等形式查看具体问题并进行修改，提升应用 的使用体验。

**起始版本：** 23

<!--Device-unnamed-declare namespace hichecker--><!--Device-unnamed-declare namespace hichecker-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
import { hichecker } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addCheckRule](arkts-performanceanalysis-hichecker-addcheckrule-f.md) | 添加一条或多条规则到系统，系统根据添加的规则进行检测或反馈，当有相应规则触发时可在hilog中grep HiChecker查看运行信息。 |
| [addRule](arkts-performanceanalysis-hichecker-addrule-f.md) |  |
| [contains](arkts-performanceanalysis-hichecker-contains-f.md) |  |
| [containsCheckRule](arkts-performanceanalysis-hichecker-containscheckrule-f.md) | 当前已添加的规则集中是否包含了某一个特定的规则。如果传入的规则级别为线程级别，则仅在当前线程中进行查询。 |
| [getRule](arkts-performanceanalysis-hichecker-getrule-f.md) | 获取当前线程规则、进程规则、告警规则的合集。 |
| [removeCheckRule](arkts-performanceanalysis-hichecker-removecheckrule-f.md) | 删除一条或多条规则，删除的规则后续将不再生效。 |
| [removeRule](arkts-performanceanalysis-hichecker-removerule-f.md) |  |

### 常量

| 名称 | 说明 |
| --- | --- |
| [RULE_CAUTION_PRINT_LOG](arkts-performanceanalysis-hichecker-con.md#rule_caution_print_log) | 告警规则，当有告警时记录日志。 |
| [RULE_CAUTION_TRIGGER_CRASH](arkts-performanceanalysis-hichecker-con.md#rule_caution_trigger_crash) | 告警规则，当有告警时让应用退出。 |
| [RULE_CHECK_ABILITY_CONNECTION_LEAK](arkts-performanceanalysis-hichecker-con.md#rule_check_ability_connection_leak) | 检测规则，检测是否发生ability泄露。 |
| [RULE_CHECK_ARKUI_PERFORMANCE](arkts-performanceanalysis-hichecker-con.md#rule_check_arkui_performance) | 检测规则，检测arkui性能。 |
| [RULE_THREAD_CHECK_NETWORK_USAGE](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_network_usage) | 检测规则，检测线程是否调用网络耗时接口。 |
| [RULE_THREAD_CHECK_SLOW_PROCESS](arkts-performanceanalysis-hichecker-con.md#rule_thread_check_slow_process) | 检测规则，检测是否有耗时函数被调用。 |

