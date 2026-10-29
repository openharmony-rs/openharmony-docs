# RawHeapDumpCallback (System API)

```TypeScript
type RawHeapDumpCallback = (code: number) => void
```

Raw heap dump callback function.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type RawHeapDumpCallback = (code: int) => void--><!--Device-unnamed-type RawHeapDumpCallback = (code: int) => void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Dump result code. <br>The value should be an integer. |
