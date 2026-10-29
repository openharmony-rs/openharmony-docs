# registerWindowLifeCycleCallback (System API)

## Modules to Import

```TypeScript
```

## registerWindowLifeCycleCallback

```TypeScript
function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean
```

Registers a callback for window lifecycle, which is invoked when a window is destroyed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean--><!--Device-jsLeakWatcherNative-function registerWindowLifeCycleCallback(cb: WindowLifeCycleCallback): boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cb | [WindowLifeCycleCallback](arkts-performanceanalysis-windowlifecyclecallback-t-sys.md) | Yes | Callback to receive the destroyed window object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the callback is registered successfully. |
