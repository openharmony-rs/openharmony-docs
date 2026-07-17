# @ohos.hilog

hilog日志系统，使应用/服务可以按照指定级别、标识和格式字符串输出日志内容，帮助开发者了解应用/服务的运行状态，更好地调试程序。

**起始版本：** 7

<!--Device-unnamed-declare namespace hilog--><!--Device-unnamed-declare namespace hilog-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

## 导入模块

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [debug](arkts-performanceanalysis-hilog-debug-f.md#debug-1) | 打印DEBUG级别的日志。DEBUG级别的日志在正式发布版本中默认不被打印，只有在调试版本或打开调试开关的情况下才会打印。 |
| [error](arkts-performanceanalysis-hilog-error-f.md#error-1) | 打印ERROR级别的日志。 |
| [fatal](arkts-performanceanalysis-hilog-fatal-f.md#fatal-1) | 打印FATAL级别的日志。 |
| [info](arkts-performanceanalysis-hilog-info-f.md#info-1) | 打印INFO级别的日志。 |
| [isLoggable](arkts-performanceanalysis-hilog-isloggable-f.md#isloggable-1) | 在打印日志前调用该接口，用于检查指定领域标识、日志标识和级别的日志是否可以打印。 |
| [setLogLevel](arkts-performanceanalysis-hilog-setloglevel-f.md#setloglevel-1) | 设置当前应用程序进程的最低日志级别。可通过prefer参数配置不同的偏好策略。如果选择策略PREFER_CLOSE_LOG，等同于调用setMinLogLevel函数。&gt; **注意：** &gt; &gt; debug版本应用下，此函数不生效。 |
| [setMinLogLevel](arkts-performanceanalysis-hilog-setminloglevel-f.md#setminloglevel-1) | 设置应用日志打印的最低日志级别，用于拦截低级别日志打印。&gt; **注意：** &gt; &gt; 如果设置的日志级别低于[全局日志级别](../../../../dfx/hilog.md#查看和设置日志级别)，设置不生效。 &gt; &gt; debug版本应用下，此函数不生效。 |
| [warn](arkts-performanceanalysis-hilog-warn-f.md#warn-1) | 打印WARN级别的日志。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | 日志级别。 |
| [PreferStrategy](arkts-performanceanalysis-hilog-preferstrategy-e.md) | 偏好策略。 |

