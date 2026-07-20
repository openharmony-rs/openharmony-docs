# setLogLevel

## 导入模块

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

<a id="setloglevel"></a>
## setLogLevel

```TypeScript
function setLogLevel(level: LogLevel, prefer: PreferStrategy): void
```

设置当前应用程序进程的最低日志级别。

可通过prefer参数配置不同的偏好策略。如果选择策略PREFER_CLOSE_LOG，等同于调用setMinLogLevel函数。

> **注意：**  
>  
> debug版本应用下，此函数不生效。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-hilog-function setLogLevel(level: LogLevel, prefer: PreferStrategy): void--><!--Device-hilog-function setLogLevel(level: LogLevel, prefer: PreferStrategy): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiLog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | 是 | 日志级别。 |
| prefer | [PreferStrategy](arkts-performanceanalysis-hilog-preferstrategy-e.md) | 是 | 偏好策略。 |

