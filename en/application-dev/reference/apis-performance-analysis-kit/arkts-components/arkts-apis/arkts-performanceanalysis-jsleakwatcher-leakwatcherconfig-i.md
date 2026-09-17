# LeakWatcherConfig

Defines the **LeakWatcherConfig** object, which contains multiple configurable properties for memory leak monitoring.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## Modules to Import

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## bgLeakCountThreshold

```TypeScript
bgLeakCountThreshold?: number
```

Threshold for the number of leak objects in a background application. Dump is triggered when this threshold is reached.

During the GC/Dump phase, dump is triggered when the value is greater than or equal to 1.

The default threshold is **1**.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## checkInterval

```TypeScript
checkInterval?: number
```

Interval between each round of leak detection, in milliseconds.

The default value is **90000ms**.

If the custom detection interval entered by the application is less than the default value, JSLeakWatcher forcibly sets the interval to the default value.

Currently, the performance overhead of JSLeakWatcher is high, which may cause application freeze. You are advised to increase the value of this parameter to reduce the freeze frequency.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## dumpHeapWaitTimeMs

```TypeScript
dumpHeapWaitTimeMs?: number
```

Delay interval for executing dump. This parameter ensures that GC can be scheduled and executed before dump. The delay interval is less than or equal to the leak detection interval, in milliseconds.

If the configured delay exceeds the leak detection interval, the delay defaults to that of the leak detection interval.

If no new leaked object exists, dump will not be triggered.

By default, the dump is performed 5 seconds after the GC ends.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

Class name of the object to be excluded from monitoring.

This parameter applies to the **Window**, **CustomComponent**, and **Ability** components and does not affect the filtering of other component types.

If obfuscation occurs, filtering cannot be performed. This parameter takes effect only in the development state.

Configuration item conflict priority: ID list &gt; trustlist.

The default value is an empty array.

**Type:** Array&lt;string&gt;

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## fgLeakCountThreshold

```TypeScript
fgLeakCountThreshold?: number
```

Threshold for the number of leaked objects in a foreground application. Dump is triggered when this threshold is reached.

During the GC/Dump phase, dump is triggered when the value is greater than or equal to 5.

The default threshold is **5**.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## maxStoredHeapDumps

```TypeScript
maxStoredHeapDumps?: number
```

Maximum number of dump files that can be saved. To prevent the disk space from being used up, the .rawheap and.jsleaklist files with the minimum timestamp are deleted when the number of dump files exceeds the maximum.

By default, 10 .rawheap files and 10 .jsleaklist files are saved.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## monitorObjectTypes

```TypeScript
monitorObjectTypes: MonitorObjectType
```

Type of the monitored object.

By default, all component types are monitored.

**Type:** [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md)

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

## objectUniqueIDs

```TypeScript
objectUniqueIDs?: Array<number>
```

List of IDs of monitored objects.

This parameter applies only to custom components and does not affect the monitoring of other component types.

For example, if the object class name ID set in the trustlist is the same as that in the custom ID list, the custom ID list takes effect.

The default value is an empty array.

**Type:** Array&lt;number&gt;

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker
