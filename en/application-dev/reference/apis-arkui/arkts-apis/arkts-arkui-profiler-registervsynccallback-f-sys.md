# registerVsyncCallback (System API)

## registerVsyncCallback

```TypeScript
function registerVsyncCallback(callback: (info: string) => void): void
```

Registers vsync callback for profiler.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (info: string) =&gt; void | Yes | the callback info is json string with ui update info. |
