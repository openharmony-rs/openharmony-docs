# dumpRawHeapSync (System API)

## Modules to Import

```TypeScript
```

## dumpRawHeapSync

```TypeScript
function dumpRawHeapSync(filePath: string): void
```

Synchronously dumps the raw heap snapshot to the given file path.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function dumpRawHeapSync(filePath: string): void--><!--Device-jsLeakWatcherNative-function dumpRawHeapSync(filePath: string): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Target file path of the raw heap snapshot. |
