# @ohos.hiviewdfx.jsLeakWatcher (ArkTS Leak Watcher)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Lutao98-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d887f892bc8a14c269d1d611c88c0769836d883f translatedAt=2026-09-21T03:00:40.304Z pushedAt=2026-09-22T01:29:30.423Z -->

This module provides the capability to monitor whether ArkTS objects leak, helping you detect and locate ArkTS object memory leaks during application development and testing.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```


## jsLeakWatcher.enable

enable(isEnable: boolean): void

Enables ArkTS object leak detection, which is disabled by default. After it is enabled, leak information is collected, which may increase performance overhead.

Recommended complete call flow: **enable()** → **watch()** → **check()** → **dump()**

When to use:
- During the application development and debugging phase, to detect and locate memory leak issues.
- During the application testing phase, to verify whether the application's memory management is normal.
- For applications with strict memory usage requirements, to continuously monitor the memory status.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| isEnable | boolean | Yes | Whether to enable **jsLeakWatcher**. **true**: Enables **jsLeakWatcher**; **false**: Disables **jsLeakWatcher**. |

**Example**

```js
jsLeakWatcher.enable(true);
```


## jsLeakWatcher.watch

watch(obj: object, msg: string): void

Registers an object to be monitored for leaks.

When to use:
- Register a key object for monitoring immediately after it is created and may leak, such as a custom component or **Window**.
- Register important objects in the application lifecycle to detect leaks in a timely manner.
- Register objects used in specific functional modules, such as **XComponent** and **NodeContainer**, to monitor their release.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| obj | object | Yes | Object to be detected.<br>**Note**: Any non-null ArkTS object can be passed in. **undefined** and primitive types are not supported. |
| msg | string | Yes | Custom object information. |

**Example**

```js
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");
```


## jsLeakWatcher.check

check(): string

Obtains the list of objects that have been registered through **jsLeakWatcher.watch** and have leaked. Objects that are not reclaimed after GC is triggered are marked as leaked.

When to use:
- Perform periodic checks during application running to detect memory leak issues in a timely manner.
- Check before and after key functions are executed to compare leak conditions.
- Locate specific leaked objects based on the leak list for code troubleshooting and fixing.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Return value**

| Type | Description |
| ------- | ---------------------------------------------------------- |
| string | List of leaked objects that are not reclaimed after GC is triggered.<br>**Note**: If **check** succeeds, a list of leaked objects in JSON format is returned; if **check** fails, an empty string is returned. |

**Example**
```js
let leakObjlist:string = jsLeakWatcher.check();
```


## jsLeakWatcher.dump

dump(filePath: string): Array&lt;string&gt;

Exports the leak list and the VM memory snapshot.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| filePath | string | Yes | Path where the generated export information file is stored.<br>**Note**: Starting from API version 24, only the latest snapshot information is retained within the process lifecycle. |

**Return value**

| Type    | Description                                                       |
| ------- | ---------------------------------------------------------- |
| Array&lt;string&gt; | Export result. It contains the leak list file with the file name extension .jsleaklist and the VM memory snapshot file with the file name extension .heapsnapshot.<br>**Note**: If the dump succeeds, the leak list file path and the VM memory snapshot path are returned; if the dump fails, an empty array is returned. |

**Example**
<!--code_no_check-->
```js
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```


## jsLeakWatcher.enableLeakWatcher<sup>20+</sup>

enableLeakWatcher(isEnabled: boolean, configs: Array&lt;string&gt;, callback: Callback&lt;Array&lt;string&gt;&gt;): void

Enables ArkTS object leak detection.

This API detects memory leaks of ArkTS objects with a single call, which is more concise than the previous method that requires calling four functions (**enable**, **watch**, **check**, and **dump**).

When to use:
- Applications with strict memory usage requirements that need continuous monitoring of memory leaks.
- Monitoring whether applications using components such as **XComponent**, **NodeContainer**, **Window**, **CustomComponent**, and **Ability** have leaks.
- Quickly identifying memory leak issues during application development, debugging, and testing phases.
- Long-running applications that need periodic memory leak detection.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | Yes | Enable status of the ArkTS object memory leak detection function. **true**: Enables the ArkTS memory leak detection function. **false**: Disables the ArkTS memory leak detection function. |
| configs | Array&lt;string&gt; | Yes | Configuration items. Each element in the array is the type of a specific object to be monitored.<br>Configurable items include: **XComponent**, **NodeContainer**, **Window**, **CustomComponent**, and **Ability**.<br>**Note**: Passing an empty array means monitoring all the objects above. |
| callback | Callback&lt;Array&lt;string&gt;&gt; | Yes | Callback function used to receive the memory leak file list and the virtual machine memory snapshot file returned by the **jsLeakWatcher.enableLeakWatcher** interface.<br>An array object is passed into the callback function. Index 0 is the leak list file name with the suffix .jsleaklist, and index 1 is the virtual machine memory snapshot file name with the suffix .rawheap. |


**Error Codes**

For details about the following error codes, see [JsLeakWatcher Error Codes](./errorcode-jsleakwatcher.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

<!--code_no_check-->
```ts
let config: Array<string> = ['XComponent'];
// Monitor the memory leak of the ArkTS object XComponent.
// Pass an empty array to monitor all objects.
jsLeakWatcher.enableLeakWatcher(true, config, (filePath: Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## jsLeakWatcher.enableLeakWatcher<sup>24+</sup>

enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback&lt;Array&lt;string&gt;&gt;): void

Enables ArkTS object leak detection.

This API detects memory leaks of ArkTS objects with a single call, which is more concise than the previous approach that required calling four functions (**enable**, **watch**, **check**, and **dump**). Through the configurable parameters in **configs**, you can customize the properties of each monitoring item, greatly improving leak detection performance compared with the previous approach.

> **NOTE**
>
> The current **jsLeakWatcher** leak detection incurs significant performance overhead, which may cause application lag. It is recommended to increase the detection interval to reduce the frequency of lag.

When to use:
- For applications with high performance requirements, parameters such as the detection interval and threshold need to be configured to balance detection accuracy and performance overhead.
- For large or complex applications, leak detection parameters such as the detection interval, leak threshold, and maximum dump count need to be finely controlled.
- For applications that use specific components (such as **CustomComponent**, **Window**, and **Ability**), the leaks of these components need to be monitored in a targeted manner.
- For applications with strict memory management requirements, filtering rules need to be configured to exclude objects that do not require monitoring.
- For applications that run for a long time or require continuous monitoring, set a reasonable detection interval and maximum number of saved files.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | Yes| Enable status of the ArkTS object memory leak detection function.<br>**true**: Enables the ArkTS memory leak detection function.<br>**false**: Disables the ArkTS memory leak detection function.|
| configs | [LeakWatcherConfig](#leakwatcherconfig24) | Yes| Object of the **LeakWatcherConfig** type, which contains multiple configurable properties for memory leak monitoring.<br>**Note**: If a parameter in the object is passed as null or a falsy value, the property is set to its default value.|
| callback | Callback&lt;Array&lt;string&gt;&gt; | Yes| Callback function used to receive the exported file paths of leak detection. The callback function receives an array object, where index 0 is the leak list file name with the .jsleaklist extension, and index 1 is the virtual machine memory snapshot file name with the .rawheap extension.|


**Error Codes**

For details about the following error codes, see [JsLeakWatcher Error Codes](./errorcode-jsleakwatcher.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

<!--code_no_check-->
```ts
// Monitor the memory leaks of the ArkTS objects CustomComponent and Window.
// Passing an empty or falsy value for a type in the object means that the property is set to its default value.
let config: jsLeakWatcher.LeakWatcherConfig = {
    monitorObjectTypes: jsLeakWatcher.MonitorObjectType.CUSTOM_COMPONENT | jsLeakWatcher.MonitorObjectType.WINDOW,
    objectUniqueIDs: [],
    checkInterval: 10000,
    fgLeakCountThreshold: 5,
    bgLeakCountThreshold: 3,
    maxStoredHeapDumps: 5,
    dumpHeapWaitTimeMs: 5000,
    exclusionList: []
};
jsLeakWatcher.enableLeakWatcher(true, config, (filePath : Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## LeakWatcherConfig<sup>24+</sup>

The **LeakWatcherConfig** object type contains multiple configurable properties for memory leak monitoring.

**System capability**: SystemCapability.HiviewDFX.HiChecker

| Name | Type | Read-only | Optional | Description | 
| ------- | ------- | ------- | ------- | ------- | 
| monitorObjectTypes | [MonitorObjectType](#monitorobjecttype24) | No | No | Type of the monitored object.<br>All component types are monitored by default. |
| objectUniqueIDs | Array&lt;number&gt; | No | Yes | List of IDs of the monitored leaked objects.<br>It applies only to custom components and does not affect the monitoring of other component types.<br>For example, when the object class name ID set in the trustlist has the same value as an ID in the custom ID list, the custom ID list parameter takes effect.<br>The default value is an empty array. |
| checkInterval | number | No | Yes | Interval between leak detection rounds, in ms. The value range is [90000, +∞).<br>The default value is 90000 ms.<br>If the custom detection interval entered by the application is smaller than the default value, jsLeakWatcher forcibly sets the interval to the default value.<br>Currently, jsLeakWatcher leak detection incurs high performance overhead and may cause application lag. It is recommended to increase this parameter to reduce the lag frequency.<br>If the value passed in is outside the value range, the default value is used. |
| fgLeakCountThreshold | number | No | Yes | When the number of leaks in the foreground reaches the configured value, a dump is triggered. The value range is [0, +∞).<br>In the GC/Dump phase, a dump is triggered when the value is greater than or equal to 5.<br>The default threshold is 5.<br>If the value passed in is outside the value range, the default value is used. |
| bgLeakCountThreshold | number | No | Yes | When the number of leaks in the background reaches the configured value, a dump is triggered. The value range is [0, +∞).<br>In the GC/Dump phase, a dump is triggered when the value is greater than or equal to 1.<br>The default threshold is 1.<br>If the value passed in is outside the value range, the default value is used. |
| maxStoredHeapDumps | number | No | Yes | Maximum number of dumps to store. The value range is (0, 10]. To prevent the disk space from being fully occupied, the rawheap and jsleaklist files with the smallest timestamps are deleted when the limit is exceeded.<br>By default, 10 rawheap files and 10 jsleaklist files are stored.<br>If the value passed in is outside the value range, the default value is used. |
| dumpHeapWaitTimeMs | number | No | Yes | Used to delay the dump execution to ensure that GC can be scheduled and completed before the dump is executed. The delay interval is less than or equal to the leak detection interval, in ms. The value range is [0, +∞).<br>If the configured delay exceeds the leak detection interval, the delay is kept consistent with the leak detection interval by default.<br>If there are no newly leaked objects, the dump is not triggered.<br>By default, the dump is executed 5 seconds after GC ends.<br>If the value passed in is outside the value range, the default value is used. |
| exclusionList | Array&lt;string&gt; | No | Yes | Used to filter out the object class names that you do not want to monitor.<br>It applies to Window, CustomComponent, and Ability components and does not affect the filtering of other component types.<br>Filtering cannot be performed when obfuscation issues exist, and it takes effect only in the development state.<br>Configuration item conflict priority: ID list > trustlist.<br>The default value is an empty array. |


## MonitorObjectType<sup>24+</sup>

Enumerates the component object types to be monitored.

**System capability**: SystemCapability.HiviewDFX.HiChecker

| Name | Value | Description |
| ------- | ------- | ------- |
| ALL | -1 | Monitors all component types. |
| CUSTOM_COMPONENT | 1 << 0 | Monitors custom component types. |
| WINDOW | 1 << 1 | Monitors Window component types. |
| NODE_CONTAINER | 1 << 2 | Monitors NodeContainer component types. |
| X_COMPONENT | 1 << 3 | Monitors XComponent component types. |
| ABILITY | 1 << 4 | Monitors Ability component types. |