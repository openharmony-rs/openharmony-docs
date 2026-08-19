# LeakWatcherConfig

LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。

**起始版本：** 26.1.0

<!--Device-jsLeakWatcher-export interface LeakWatcherConfig--><!--Device-jsLeakWatcher-export interface LeakWatcherConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## bgLeakCountThreshold

```TypeScript
bgLeakCountThreshold?: int
```

应用在后台泄漏个数达到设定值触发dump，取值范围为[0, +∞)。 GC/Dump阶段，大于等于1时触发Dump。 阈值默认为1。 传入不在取值范围内的值时将使用默认值。

**类型：** int

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-bgLeakCountThreshold?: int--><!--Device-LeakWatcherConfig-bgLeakCountThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## checkInterval

```TypeScript
checkInterval?: int
```

每轮泄漏检测间隔时间，单位：ms，取值范围为[90000, +∞)。 默认为90000ms。 如果应用输入的自定义检测间隔时间小于默认值，JSLeakWatcher强制将间隔设置为默认值。 当前jsLeakWatcher泄漏检测性能开销较大，会导致应用卡顿，建议增大该参数，减少卡顿频率。 传入不在取值范围内的值时将使用默认值。

**类型：** int

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-checkInterval?: int--><!--Device-LeakWatcherConfig-checkInterval?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## dumpHeapWaitTimeMs

```TypeScript
dumpHeapWaitTimeMs?: int
```

延迟执行dump，保证GC能调度且执行完再执行dump，延迟间隔小于等于泄漏检测间隔时间，单位：ms，取值范围为[0, +∞)。 设置延迟时长超过泄漏间隔时长则默认与泄漏间隔时长保持一致。 若无新增泄漏对象将不会触发dump。 GC结束后默认延迟5秒执行dump。 传入不在取值范围内的值时将使用默认值。

**类型：** int

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-dumpHeapWaitTimeMs?: int--><!--Device-LeakWatcherConfig-dumpHeapWaitTimeMs?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

过滤不想监测的对象类名。 作用于Window、CustomComponent和Ability组件，不会影响其他组件类型的过滤。 存在混淆问题时无法进行过滤，只在开发态生效。 配置项冲突优先级：ID列表 > 白名单。 默认为空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-exclusionList?: Array<string>--><!--Device-LeakWatcherConfig-exclusionList?: Array<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## fgLeakCountThreshold

```TypeScript
fgLeakCountThreshold?: int
```

应用在前台泄漏个数达到设定值触发dump，取值范围为[0, +∞)。 GC/Dump阶段，大于等于5时触发Dump。 阈值默认为5。 传入不在取值范围内的值时将使用默认值。

**类型：** int

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-fgLeakCountThreshold?: int--><!--Device-LeakWatcherConfig-fgLeakCountThreshold?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## maxStoredHeapDumps

```TypeScript
maxStoredHeapDumps?: int
```

最大dump保存个数，取值范围为(0, 10]，避免磁盘空间占满，超过则删除时间戳最小的rawheap、jsleaklist文件。 默认保存10个rawheap、10个jsleaklist文件。 传入不在取值范围内的值时将使用默认值。

**类型：** int

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-maxStoredHeapDumps?: int--><!--Device-LeakWatcherConfig-maxStoredHeapDumps?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## monitorObjectTypes

```TypeScript
monitorObjectTypes: MonitorObjectType
```

被监测对象类型。 默认监测所有组件类型。

**类型：** [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md)

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-monitorObjectTypes: MonitorObjectType--><!--Device-LeakWatcherConfig-monitorObjectTypes: MonitorObjectType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## objectUniqueIDs

```TypeScript
objectUniqueIDs?: Array<int>
```

被监测泄漏对象ID列表。 只作用于自定义组件，不会影响其他组件类型的监测。 例如：白名单中设置的对象类名ID与自定义ID列表存在相同值时，生效自定义ID列表参数。 默认为空数组。

**类型：** Array&lt;int&gt;

**起始版本：** 26.1.0

<!--Device-LeakWatcherConfig-objectUniqueIDs?: Array<int>--><!--Device-LeakWatcherConfig-objectUniqueIDs?: Array<int>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

