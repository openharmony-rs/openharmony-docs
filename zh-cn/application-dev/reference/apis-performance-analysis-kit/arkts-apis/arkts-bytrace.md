# @ohos.bytrace(性能打点)

本模块提供了追踪进程轨迹的能力，用于应用性能分析场景。开发者可以通过性能打点来追踪关键代码段的执行时间，定位性能瓶颈，优化应用性能。适用于应用启 动耗时分析、业务流程性能监控、帧率分析等场景。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [hiTraceMeter](arkts-hitracemeter.md)

<!--Device-unnamed-declare namespace bytrace--><!--Device-unnamed-declare namespace bytrace-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishTrace(性能打点)](arkts-performanceanalysis-bytrace-finishtrace-f.md) | 标记一个时间片跟踪事件的结束。 |
| [startTrace(性能打点)](arkts-performanceanalysis-bytrace-starttrace-f.md) | 标记一个时间片跟踪任务的开始。 如果有多个相同name的任务需要追踪或者对同一个任务要追踪多次，并且这些跟踪任务会同时被执行，则每次调用startTrace的taskId必须不一致。如果 具有相同name的跟踪任务是串行执行的，则taskId可以相同。在下面bytrace.finishTrace的示例中会举例说明。 |
| [traceByValue(性能打点)](arkts-performanceanalysis-bytrace-tracebyvalue-f.md) | 标记预追踪耗时任务的数值变量，该变量的数值会不断变化。traceByValue可独立使用，用于记录某个数值变量的变化轨迹。 |

