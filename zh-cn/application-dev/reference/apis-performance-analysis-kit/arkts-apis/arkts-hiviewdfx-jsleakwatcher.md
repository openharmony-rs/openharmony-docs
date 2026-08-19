# @ohos.hiviewdfx.jsLeakWatcher

本模块提供了监控ArkTS对象是否发生泄漏的能力，可在应用开发、测试阶段发现并定位ArkTS对象的内存泄漏问题。

**起始版本：** 26.1.0

<!--Device-unnamed-declare namespace jsLeakWatcher--><!--Device-unnamed-declare namespace jsLeakWatcher-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [check](arkts-performanceanalysis-jsleakwatcher-check-f.md) | 获取已通过jsLeakWatcher.watch注册发生泄漏的对象列表，触发GC后未被回收的对象会被标记为泄漏。 |
| [dump](arkts-performanceanalysis-jsleakwatcher-dump-f.md) | 导出泄漏列表和虚拟机内存快照。 |
| [enable](arkts-performanceanalysis-jsleakwatcher-enable-f.md) | 使能ArkTS对象泄漏检测，默认关闭。开启后会收集泄漏信息，可能增加性能开销。 |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | 使能ArkTS对象泄漏检测。 此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁。 |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | 使能ArkTS对象泄漏检测。 此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁；通过configs可配置项参数，自定义设置监测项各属性，相比较之前极大提升了泄漏检测性能。 > **注意** > > 当前jsLeakWatcher泄漏检测性能开销较大，会导致应用卡顿，建议增大检测间隔时间，减少卡顿频率。 |
| [watch](arkts-performanceanalysis-jsleakwatcher-watch-f.md) | 注册待检测泄漏的对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md) | 需要监控的组件对象类型枚举。 |

