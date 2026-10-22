# ExternalLogContainer

```TypeScript
class ExternalLogContainer
```

一个外部日志容器，包含所有外部日志文件。

**起始版本：** 26.0.1

<!--Device-hiAppEvent-class ExternalLogContainer--><!--Device-hiAppEvent-class ExternalLogContainer-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## getAllLogFiles

```TypeScript
getAllLogFiles(): Set<string>
```

获取所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getAllLogFiles(): Set<string>--><!--Device-ExternalLogContainer-getAllLogFiles(): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 所有外部日志文件路径的集合 |

## getAllLogs

```TypeScript
getAllLogs(): Set<ExternalLogWrapper>
```

获取所有ExternalLogWrappers的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getAllLogs(): Set<ExternalLogWrapper>--><!--Device-ExternalLogContainer-getAllLogs(): Set<ExternalLogWrapper>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;[ExternalLogWrapper](arkts-performanceanalysis-hiappevent-externallogwrapper-c.md)&gt; | 所有ExternalLogWrappers的集合 |

## getFirstGeneratedLogFiles

```TypeScript
getFirstGeneratedLogFiles(num: number): Set<string>
```

获取给定数字的最早生成的外部日志文件路径

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getFirstGeneratedLogFiles(num: int): Set<string>--><!--Device-ExternalLogContainer-getFirstGeneratedLogFiles(num: int): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| num | number | 是 | 给定查询文件的个数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 符合条件的外部日志文件路径的集合 |

## getLogFilesGeneratedAfter

```TypeScript
getLogFilesGeneratedAfter(timePoint: number): Set<string>
```

获取给定时间之后的所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogFilesGeneratedAfter(timePoint: long): Set<string>--><!--Device-ExternalLogContainer-getLogFilesGeneratedAfter(timePoint: long): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timePoint | number | 是 | 给定的文件生成时间点（单位：毫秒） |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 指定时间之后的所有外部日志文件路径的集合 |

## getLogFilesGeneratedBefore

```TypeScript
getLogFilesGeneratedBefore(timePoint: number): Set<string>
```

获取给定时间之前的所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogFilesGeneratedBefore(timePoint: long): Set<string>--><!--Device-ExternalLogContainer-getLogFilesGeneratedBefore(timePoint: long): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timePoint | number | 是 | 给定的文件生成时间点（单位：毫秒） |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 给定时间之前的所有外部日志文件路径的集合 |

## getLogFilesLargerThan

```TypeScript
getLogFilesLargerThan(sizeKb: number): Set<string>
```

获取大小大于给定数量的所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogFilesLargerThan(sizeKb: long): Set<string>--><!--Device-ExternalLogContainer-getLogFilesLargerThan(sizeKb: long): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sizeKb | number | 是 | 给定的文件大小 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 大小大于给定数量的所有外部日志文件路径的集合 |

## getLogFilesOfSysEvent

```TypeScript
getLogFilesOfSysEvent(event: string): Set<string>
```

获取给定系统事件的所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogFilesOfSysEvent(event: string): Set<string>--><!--Device-ExternalLogContainer-getLogFilesOfSysEvent(event: string): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 给定系统事件的字符串 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 给定系统事件的所有外部日志文件路径的集合 |

## getLogFilesSmallerThan

```TypeScript
getLogFilesSmallerThan(sizeKb: number): Set<string>
```

获取大小小于给定数量的所有外部日志文件路径的集合

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogFilesSmallerThan(sizeKb: long): Set<string>--><!--Device-ExternalLogContainer-getLogFilesSmallerThan(sizeKb: long): Set<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sizeKb | number | 是 | 给定的文件大小 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Set&lt;string&gt; | 大小小于给定数量的所有外部日志文件路径的集合 |

## getLogNumber

```TypeScript
getLogNumber(): number
```

获取所有外部日志文件的个数

**起始版本：** 26.0.1

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ExternalLogContainer-getLogNumber(): int--><!--Device-ExternalLogContainer-getLogNumber(): int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 所有外部日志文件的个数 |
