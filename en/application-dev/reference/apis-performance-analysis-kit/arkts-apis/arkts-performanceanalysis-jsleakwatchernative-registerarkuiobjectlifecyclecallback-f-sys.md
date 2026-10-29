# registerArkUIObjectLifeCycleCallback (System API)

## Modules to Import

```TypeScript
```

## registerArkUIObjectLifeCycleCallback

```TypeScript
function registerArkUIObjectLifeCycleCallback(cb: WeakRefCallback): boolean
```

Registers a callback for ArkUI object lifecycle, which is invoked with a weak reference when the object is destroyed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function registerArkUIObjectLifeCycleCallback(cb: WeakRefCallback): boolean--><!--Device-jsLeakWatcherNative-function registerArkUIObjectLifeCycleCallback(cb: WeakRefCallback): boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cb | [WeakRefCallback](arkts-performanceanalysis-weakrefcallback-t-sys.md) | Yes | Callback to receive the weak reference of the destroyed object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the callback is registered successfully. |
