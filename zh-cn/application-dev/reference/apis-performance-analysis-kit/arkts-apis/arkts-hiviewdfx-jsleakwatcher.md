# @ohos.hiviewdfx.jsLeakWatcher

本模块提供了监控ArkTS对象是否发生泄漏的能力，可在应用开发、测试阶段发现并定位ArkTS对象的内存泄漏问题。

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [check](arkts-performanceanalysis-jsleakwatcher-check-f.md) | 获取已通过jsLeakWatcher.watch注册发生泄漏的对象列表，触发GC后未被回收的对象会被标记为泄漏。 |
| [dump](arkts-performanceanalysis-jsleakwatcher-dump-f.md) | 导出泄漏列表和虚拟机内存快照。 |
| [enable](arkts-performanceanalysis-jsleakwatcher-enable-f.md) | 使能ArkTS对象泄漏检测，默认关闭。开启后会收集泄漏信息，可能增加性能开销。推荐的完整调用流程：enable() → watch() → check() → dump()使用场景：  - 应用开发调试阶段，用于检测和定位内存泄漏问题。  - 应用测试阶段，用于验证应用的内存管理是否正常。  - 对内存使用有严格要求的应用，需要持续监控内存状态。 |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | 使能ArkTS对象泄漏检测。此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁。使用场景：  - 对内存使用有严格要求的应用，需要持续监控内存泄漏情况。  - 监控使用XComponent、NodeContainer、Window、CustomComponent、Ability等组件的应用是否发生泄漏。  - 应用开发调试和测试阶段，快速发现内存泄漏问题。  - 长时间运行的应用，需要定期检测内存泄漏。 |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | 使能ArkTS对象泄漏检测。此接口通过一次调用即可检测ArkTS对象的内存泄漏，比之前需要调用四个函数（enable、watch、check、dump）的方法更加简洁；通过configs可配置项参数，自定义设置监测项各属性，相比较之前极大提升了泄漏检测性能。 |
| [watch](arkts-performanceanalysis-jsleakwatcher-watch-f.md) | 注册待检测泄漏的对象。使用场景：  - 在创建可能发生泄漏的关键对象后（如自定义组件、Window等），立即注册进行监控。  - 对应用生命周期中的重要对象进行注册，以便及时发现泄漏。  - 在特定功能模块中使用到的对象，如XComponent、NodeContainer等，注册以监控其释放情况。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md) | 需要监控的组件对象类型枚举。 |
