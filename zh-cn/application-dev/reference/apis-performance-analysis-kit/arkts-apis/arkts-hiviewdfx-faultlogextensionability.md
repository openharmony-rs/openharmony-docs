# @ohos.hiviewdfx.FaultLogExtensionAbility

## 导入模块

```TypeScript
import { FaultLogExtensionAbility } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FaultLogExtensionAbility](arkts-performanceanalysis-hiviewdfx-faultlogextensionability-faultlogextensionability-c.md) | 本模块实现故障的延迟通知功能。[HiAppEvent](arkts-performanceanalysis-hiappevent-n.md)订阅崩溃、应用冻屏事件时，只有当应用下次启动后才能接收上一次的事件。如果应用无法启动或长时间未打开，则存在故障无法及时上报的局限性。本模块作为该场景的补充。在应用实现FaultLogExtensionAbility后，当应用发生崩溃或冻屏时，系统服务预计会在30分钟后拉起FaultLogExtensionAbility。开发者可在[onFaultReportReady](arkts-performanceanalysis-hiviewdfx-faultlogextensionability-faultlogextensionability-c.md#onfaultreportready-1)中订阅并处理故障事件。 |

