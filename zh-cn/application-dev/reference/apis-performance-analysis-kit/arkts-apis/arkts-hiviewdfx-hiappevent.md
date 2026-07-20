# @ohos.hiviewdfx.hiAppEvent

本模块提供应用打点和事件订阅能力，包括事件存储、事件订阅、事件清理、打点配置等功能。HiAppEvent将应用运行过程中触发的事件信息统一归纳到[AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md)中，并将事件分为系统事件和应用事件两类。

系统事件来源于系统服务，是系统预先定义的事件，这类事件信息中的事件参数对象params包含的字段已由各系统事件定义，具体字段含义在各系统事件指南的介绍中，例如[崩溃事件介绍](docroot://dfx/hiappevent-watcher-crash-events.md)。

应用事件来源于应用，是应用开发者自己定义的事件，这类事件信息支持自定义后通过[Write](arkts-performanceanalysis-hiappevent-write-f.md#write-1)打点接口进行配置设定，具体字段含义可结合开发者需求展开。

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [hiAppEvent](arkts-performanceanalysis-hiappevent-n.md) | 本模块提供应用打点和事件订阅能力，包括事件存储、事件订阅、事件清理、打点配置等功能。HiAppEvent将应用运行过程中触发的事件信息统一归纳到[AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md)中，并将事件分为系统事件和应用事件两类。  系统事件来源于系统服务，是系统预先定义的事件，这类事件信息中的事件参数对象params包含的字段已由各系统事件定义，具体字段含义在各系统事件指南的介绍中，例如[崩溃事件介绍](docroot://dfx/hiappevent-watcher-crash-events.md)。  应用事件来源于应用，是应用开发者自己定义的事件，这类事件信息支持自定义后通过[Write](arkts-performanceanalysis-hiappevent-write-f.md#write-1)打点接口进行配置设定，具体字段含义可结合开发者需求展开。 |

