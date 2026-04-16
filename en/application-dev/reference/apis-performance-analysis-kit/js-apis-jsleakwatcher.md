# @ohos.hiviewdfx.jsLeakWatcher (JS Leak Detection)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @lu_tao-->
<!--Designer: @martin_duan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

This module provides the capability of monitoring whether JS objects are leaked.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```


## jsLeakWatcher.enable

enable(isEnable: boolean): void

Enables the detection for JS object leaks. This function is disabled by default.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| isEnable | boolean | Yes| Whether to enable **jsLeakWatcher**. **true**: yes; **false**: no.|

**Example**

```js
jsLeakWatcher.enable(true);
```


## jsLeakWatcher.watch

watch(obj: object, msg: string): void

Registers the object to be checked.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | object | Yes| Name of the object to be checked.<br>Note: You can pass objects of any type.|
| msg | string | Yes| Custom object information.|

**Example**

```js
let obj:Object = new Object();
jsLeakWatcher.watch(obj, "Trace Object");
```


## jsLeakWatcher.check

check(): string

Obtains the list of objects that are leaked and registered using **jsLeakWatcher.watch()**. Objects that are not reclaimed after GC is triggered are marked as leaked.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Return value**

| Type   | Description                                                      |
| ------- | ---------------------------------------------------------- |
| string | List of leaked objects that are not reclaimed after GC is triggered.<br>Note: If this API is successful, a list of leaked objects in JSON format is returned. Otherwise, an empty string is returned.|

**Example**
```js
let leakObjlist:string = jsLeakWatcher.check();
```


## jsLeakWatcher.dump

dump(filePath: string): Array&lt;string&gt;

Dumps the list of leaked objects and VM memory snapshot.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| filePath | string | Yes| Path for storing exported information files.|

**Return value**

| Type   | Description                                                      |
| ------- | ---------------------------------------------------------- |
| Array&lt;string&gt; | Export result. The file name extension is **.jsleaklist** for the list of leaked objects and **.heapsnapshot** for the VM memory snapshot.<br>Note: If the dump is successful, the path of the leaked object list file and the VM memory snapshot path are returned. Otherwise, an empty array is returned.|

**Example**
<!--code_no_check-->
```js
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```


## jsLeakWatcher.enableLeakWatcher<sup>20+</sup>

enableLeakWatcher(isEnabled: boolean, configs: Array&lt;string&gt;, callback: Callback&lt;Array&lt;string&gt;&gt;): void

Enables the detection for JS object leaks. This function is disabled by default.

This API can detect the JS object memory leak, which is simpler than the method that needs to call the **enable**, **watch**, **check**, and **dump** functions.

If a memory leak occurs, the leaked file is returned through the callback.


**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | Yes| Whether to enable the detection for JS object memory leaks. **true**: yes; **false**: no.|
| configs | Array&lt;string&gt; | Yes| Configuration item. Each element in the array indicates a specific object type to monitor.<br>Options: **XComponent**, **NodeContainer**, **Window**, **CustomComponent**, and **Ability**.<br>Note: An empty array indicates that all the preceding objects are monitored.|
| callback | Callback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to receive the memory-leaked object returned by the **jsLeakWatcher.enableLeakWatcher** API.<br>You need to input an array object in the callback. Index **0** is the name of the leak list file, whose extension is **.jsleaklist**. Index **1** is the name of the VM memory snapshot file, whose extension is **.rawheap**.|


**Error codes**

For details, see [JsLeakWatcher Error Codes](./errorcode-jsleakwatcher.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

<!--code_no_check-->
```ts
let config: Array<string> = ['XComponent'];
// Monitor the memory leak of the JS object XComponent.
// If an empty array is passed, all objects are monitored.
jsLeakWatcher.enableLeakWatcher(true, config, (filePath: Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## jsLeakWatcher.enableLeakWatcher<sup>24+</sup>

enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback&lt;Array&lt;string&gt;&gt;): void

Enables the ArkTS object leak detection.

This API can detect memory leaks of ArkTS objects with a single call, which is simpler than the previous method that requires four functions (**enable**, **watch**, **check**, and **dump**). You can use the **configs** parameter to customize the properties of monitoring items, greatly improving the leak detection performance.

**System capability**: SystemCapability.HiviewDFX.HiChecker

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| isEnabled | boolean | Yes| Whether to enable the detection for ArkTS object memory leaks.<br>**true**: yes;<br>**false**: no.|
| configs | [LeakWatcherConfig](#leakwatcherconfig) | Yes| LeakWatcherConfig object, which contains multiple configurable properties for memory leak monitoring.<br>Note: If the parameter type in the object is set to null or a false value, the default value is used.|
| callback | Callback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to receive the memory-leaked object returned by the **jsLeakWatcher.enableLeakWatcher** API.<br>You need to input an array object in the callback. Index **0** is the name of the leak list file, whose extension is **.jsleaklist**. Index **1** is the name of the VM memory snapshot file, whose extension is **.rawheap**.|


**Error codes**

For details, see [JsLeakWatcher Error Codes](./errorcode-jsleakwatcher.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 10801001 | The parameter isEnabled is invalid.                              |
| 10801002 | The parameter config is invalid.                                 |
| 10801003 | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

<!--code_no_check-->
```ts
enum MonitorObjectType {
  ALL = -1, 
  CUSTOM_COMPONENT = 1 << 0,
  WINDOW = 1 << 1,
  NODE_CONTAINER = 1 << 2,
  X_COMPONENT = 1 << 3,
  ABILITY = 1 << 4
};

// Detect memory leaks of the ArkTS objects CustomComponent and Window.
// If the value of an object type is null or false, the default value is used.
let config: LeakWatcherConfig = {
    monitorObjectTypes: MonitorObjectType.CUSTOM_COMPONENT | MonitorObjectType.WINDOW,
    objectUniqueIDs: [],
    checkInterval: 10000,
    fgLeakCountThreshold: 5,
    bgLeakCountThreshold: 3,
    maxStoredHeapDumps: 5,
    dumpHeapWaitTimeMs: 5000,
    exclusionList: []
};
jsLeakWatcher.enableLeakWatcher(true, config, (filepath : Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```


## LeakWatcherConfig

Defines the **LeakWatcherConfig** object, which contains multiple configurable properties for memory leak monitoring.

**System capability**: SystemCapability.HiviewDFX.HiChecker

| Name| Type| Read-Only| Optional| Description| 
| ------- | ------- | ------- | ------- | ------- | 
| monitorObjectTypes | [MonitorObjectType](#monitorobjecttype) | No| No| Type of the monitored object.<br>By default, all component types are monitored.|
| objectUniqueIDs | Array&lt;number&gt; | No  | Yes  | List of IDs of monitored objects.<br>This parameter applies only to custom components and does not affect the monitoring of other component types.<br>For example, if the object class name ID set in the trustlist is the same as that in the custom ID list, the custom ID list takes effect.<br>The default value is an empty array.|
| checkInterval | number | No| Yes| Interval between each round of leak detection, in milliseconds.<br>The default value is 30 seconds.|
| fgLeakCountThreshold | number | No| Yes| Threshold for the number of leaked objects in a foreground application. Dump is triggered when this threshold is reached.<br>During the GC/Dump phase, dump is triggered when the value is greater than or equal to 5.<br>The default threshold is **5**.|
| bgLeakCountThreshold | number | No| Yes| Threshold for the number of leak objects in a background application. Dump is triggered when this threshold is reached.<br>During the GC/Dump phase, dump is triggered when the value is greater than or equal to 1.<br>The default threshold is **1**.|
| maxStoredHeapDumps | number | No| Yes| Maximum number of dump files that can be saved. To prevent the disk space from being used up, the .rawheap and .jsleaklist files with the minimum timestamp are deleted when the number of dump files exceeds the maximum.<br>By default, 10 .rawheap files and 10 .jsleaklist files are saved.|
| dumpHeapWaitTimeMs | number | No| Yes| Delay interval for executing dump. This parameter ensures that GC can be scheduled and executed before dump. The delay interval is less than or equal to the leak detection interval, in milliseconds.<br>If the configured delay exceeds the leak detection interval, the delay defaults to that of the leak detection interval.<br>If no new leaked object exists, dump will not be triggered.<br>By default, the dump is performed 5 seconds after the GC ends.|
| exclusionList | Array&lt;string&gt; | No| Yes| Class name of the object to be excluded from monitoring.<br>This parameter applies only to custom components and does not affect the filtering of other component types.<br>If obfuscation occurs, filtering cannot be performed. This parameter takes effect only in the development state.<br>Configuration item conflict priority: ID list > trustlist.<br>The default value is an empty array.|


## MonitorObjectType

Enumerates the types of component objects to be monitored.

**System capability**: SystemCapability.HiviewDFX.HiChecker

| Name| Value| Description|
| ------- | ------- | ------- |
| ALL | -1 | All component types are monitored.|
| CUSTOM_COMPONENT | 1 << 0 | Custom component types are monitored.|
| WINDOW | 1 << 1 | The **Window** component type is monitored.|
| NODE_CONTAINER | 1 << 2 | The **NodeContainer** component type is monitored.|
| X_COMPONENT | 1 << 3 | The **XComponent** component type is monitored.|
| ABILITY | 1 << 4 | The **Ability** component type is monitored.|
