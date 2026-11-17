# markLifecycleEnded

## Modules to Import

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## markLifecycleEnded

```TypeScript
function markLifecycleEnded(obj: object): void
```

Marks an object as a lifecycle-ended object. If a developer determines that an object should no longer be used or referenced, the developer uses this API to mark the object before releasing it. When an OOM fault occurs, if the attributes of an object in the exported heap snapshot file contain the __ohosDfxJsLeakMarker attribute, the object is not released as expected.

> **NOTE:** 
> Since a single marking operation incurs a small amount of memory overhead, we recommend marking only the objects suspected of leakage or performing marking only in grayscale scenarios, and avoiding extensive marking in normal scenarios.

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-jsLeakWatcher-function markLifecycleEnded(obj: object): void--><!--Device-jsLeakWatcher-function markLifecycleEnded(obj: object): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | object | Yes | Object to be marked as lifecycle-ended. <br>Value constraint: 1: non-null value 2: non-undefined value 3: non-primitive value. |
