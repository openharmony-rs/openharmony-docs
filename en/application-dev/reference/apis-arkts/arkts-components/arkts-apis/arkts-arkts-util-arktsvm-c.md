# ArkTSVM

A class that provides VM maintenance and test capabilities for developers.

**Since:** 23

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## enableLocalHandleDetection

```TypeScript
static enableLocalHandleDetection(): void
```

Enable the local handle detection to avoid memory leakage in the event looper of Libuv or EventHandler.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## getAllVMHeapMemoryInfo

```TypeScript
static getAllVMHeapMemoryInfo(): Promise<HeapMemoryInfo[]>
```

Get all heap memory information from ArkTS-VMs and the shared heap.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HeapMemoryInfo](arkts-arkts-util-heapmemoryinfo-i.md)[]&gt; | Returns a promise containing all the heap memory information from ArkTS-VMs' local heap and the shared heap. |

## offVMHeapMemoryPressure

```TypeScript
static offVMHeapMemoryPressure(): void
```

Unregister the callback that is triggered when the heap memory exceeds the critical warning threshold after a GC.

@static

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## onVMHeapMemoryPressure

```TypeScript
static onVMHeapMemoryPressure(callback: Callback<string>, heapMemoryThreshold: HeapMemoryThreshold): boolean
```

Register a callback that is triggered if the heap memory exceeds the critical warning threshold after a GC. It must be called on the main thread and only one callback can be registered.

NOTE: There is no guarantee that the callback will be triggered before OOM.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | This callback is triggered if the memory reaches the threshold after a GC. The string parameter indicates the type of memory pressure event:"LocalHeapMemPressure", "SharedHeapMemPressure", or "ProcessHeapMemPressure". |
| heapMemoryThreshold | [HeapMemoryThreshold](arkts-arkts-util-heapmemorythreshold-i.md) | Yes | Indicates the percentage threshold of the heap memory to trigger the callback after a GC. The value range is [70, 95]. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the registration succeeds; returns `false` if not called on the main thread or if the callback is already registered. @static |

## setMultithreadingDetectionEnabled

```TypeScript
static setMultithreadingDetectionEnabled(enabled: boolean, options?: MultithreadingDetectionOptions):void
```

Sets whether to enable multithreading detection. When **enabled** is set to **true**, the detection is turned on, and multithreading-related details will be included in the cppcrash files generated for multithreading issues. When **enabled** is set to **false**, the detection is turned off, and no such details will be present in the corresponding cppcrash files.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Controls whether to enable multithreading detection. **true** means enabling the detection, and **false** means disabling it. |
| options | [MultithreadingDetectionOptions](arkts-arkts-util-multithreadingdetectionoptions-i.md) | No | Optional configuration items<br>**Since:** 26.0.0 |

**Examples**

```TypeScript
import { util } from '@kit.ArkTS';

// Enable multithreading detection.
util.ArkTSVM.setMultithreadingDetectionEnabled(true);
// Disable multithreading detection.
util.ArkTSVM.setMultithreadingDetectionEnabled(false);
```

## setTrackGlobalRef

```TypeScript
static setTrackGlobalRef(enable: boolean): void
```

Enable or disable tracking of the relationship between napi_ref and global handle. When enabled, heap snapshot will include native reference address information. When disabled (enable is false), the tracking will be stopped and heap snapshot will not display the relationship between native reference and global handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | The boolean flag enable to Indicates whether to turn on or off tracking, **true** means to turn on tracking, and **false** means to turn off it. |
