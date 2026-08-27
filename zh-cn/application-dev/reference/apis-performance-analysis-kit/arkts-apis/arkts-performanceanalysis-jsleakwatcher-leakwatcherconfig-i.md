# LeakWatcherConfig

LeakWatcherConfig对象类型，对象中包含多个用于内存泄漏监测的可配置属性。

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## 导入模块

```TypeScript
```

## bgLeakCountThreshold

```TypeScript
bgLeakCountThreshold?: number
```

应用在后台泄漏个数达到设定值触发dump。GC/Dump阶段，大于等于1时触发Dump。阈值默认为1。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## checkInterval

```TypeScript
checkInterval?: number
```

每轮泄漏检测间隔时间，单位：ms，取值范围为[90000, +∞)。默认为90000ms。如果应用输入的自定义检测间隔时间小于默认值，jsLeakWatcher强制将间隔设置为默认值。当前jsLeakWatcher泄漏检测性能开销较大，会导致应用卡顿，建议增大该参数，减少卡顿频率。传入不在取值范围内的值时将使用默认值。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## dumpHeapWaitTimeMs

```TypeScript
dumpHeapWaitTimeMs?: number
```

延迟执行dump，保证GC能调度且执行完再执行dump，延迟间隔小于等于泄漏检测间隔时间，单位：ms。设置延迟时长超过泄漏间隔时长则默认与泄漏间隔时长保持一致。若无新增泄漏对象将不会触发dump。GC结束后默认延迟5秒执行dump。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

过滤不想监测的对象类名。作用于Window、CustomComponent和Ability组件，不会影响其他组件类型的过滤。存在混淆问题时无法进行过滤，只在开发态生效。配置项冲突优先级：ID列表 &gt; 白名单。默认为空数组。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## fgLeakCountThreshold

```TypeScript
fgLeakCountThreshold?: number
```

应用在前台泄漏个数达到设定值触发dump。GC/Dump阶段，大于等于5时触发Dump。阈值默认为5。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## maxStoredHeapDumps

```TypeScript
maxStoredHeapDumps?: number
```

最大dump保存个数，避免磁盘空间占满，超过则删除时间戳最小的rawheap、jsleaklist文件。默认保存10个rawheap、10个jsleaklist文件。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## monitorObjectTypes

```TypeScript
monitorObjectTypes: MonitorObjectType
```

被监测对象类型。默认监测所有组件类型。

**类型：** [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md)

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker

## objectUniqueIDs

```TypeScript
objectUniqueIDs?: Array<number>
```

被监测泄漏对象ID列表。只作用于自定义组件，不会影响其他组件类型的监测。例如：白名单中设置的对象类名ID与自定义ID列表存在相同值时，生效自定义ID列表参数。默认为空数组。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**系统能力：** SystemCapability.HiviewDFX.HiChecker
