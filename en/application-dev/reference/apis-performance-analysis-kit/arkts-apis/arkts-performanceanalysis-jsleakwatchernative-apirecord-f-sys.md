# apiRecord (System API)

## Modules to Import

```TypeScript
```

## apiRecord

```TypeScript
function apiRecord(name: string): void
```

Records the API call metric. Only takes effect when API metrics are enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function apiRecord(name: string): void--><!--Device-jsLeakWatcherNative-function apiRecord(name: string): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the API to record. |
