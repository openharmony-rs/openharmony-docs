# enableLeakWatcher

## Modules to Import

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## enableLeakWatcher

```TypeScript
function enableLeakWatcher(isEnabled: boolean, configs: Array<string>, callback: Callback<Array<string>>): void
```

Enables the ArkTS object leak detection.

This API can detect the ArkTS object memory leak, which is simpler than the method that needs to call the **enable**, **watch**, **check**, and **dump** functions.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable the detection for ArkTS object memory leaks. **true**: yes; **false**: no. |
| configs | Array&lt;string&gt; | Yes | Configuration item. Each element in the array indicates a specific object type to monitor.<br>Options: **XComponent**, **NodeContainer**, **Window**, **CustomComponent**, and **Ability**. <br>Note: An empty array indicates that all the preceding objects are monitored. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to receive the memory-leaked object returned by the **jsLeakWatcher.enableLeakWatcher** API.<br>You need to input an array object in the callback. Index **0** is the name of the leak list file, whose extension is **.jsleaklist**. Index **1** is the name of the VM memory snapshot file, whose extension is **.rawheap**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001-invalid-isenabled) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002-invalid-config) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003-invalid-callback) | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
let config: Array<string> = ['XComponent'];
// Monitor the memory leak of the ArkTS object XComponent.
// If an empty array is passed, all objects are monitored.
jsLeakWatcher.enableLeakWatcher(true, config, (filePath: Array<string>) => {
    console.info('JsLeakWatcher leaklistFileName:' + filePath[0]);
    console.info('JsLeakWatcher heapDumpFileName:' + filePath[1]);
});
```

```TypeScript
// Detect memory leaks of the ArkTS objects CustomComponent and Window.
// If the value of an object type is null or false, the default value is used.
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


## enableLeakWatcher

```TypeScript
function enableLeakWatcher(isEnabled: boolean, configs: LeakWatcherConfig, callback: Callback<Array<string>>): void
```

Enables the ArkTS object leak detection.

This API can detect memory leaks of ArkTS objects with a single call, which is simpler than the previous method that requires four functions (**enable**, **watch**, **check**, and **dump**). You can use the **configs** parameter to customize the properties of monitoring items, greatly improving the leak detection performance.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isEnabled | boolean | Yes | Whether to enable the detection for ArkTS object memory leaks.<br>**true**: yes; <br>**false**: no. |
| configs | [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | Yes | LeakWatcherConfig object, which contains multiple configurable properties for memory leak monitoring.<br>Note: If the parameter type in the object is set to null or a false value, the default value is used. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to receive the memory-leaked object returned by the **jsLeakWatcher.enableLeakWatcher** API.<br>You need to input an array object in the callback. Index **0** is the name of the leak list file, whose extension is **.jsleaklist**. Index **1** is the name of the VM memory snapshot file, whose extension is **.rawheap**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10801001](../errorcode-jsleakwatcher.md#10801001-invalid-isenabled) | The parameter isEnabled is invalid. |
| [10801002](../errorcode-jsleakwatcher.md#10801002-invalid-config) | The parameter config is invalid. |
| [10801003](../errorcode-jsleakwatcher.md#10801003-invalid-callback) | The parameter callback is invalid. Input parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

See [enableLeakWatcher](#enableleakwatcher)
