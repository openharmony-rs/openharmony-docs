# WatermarkCallback

```TypeScript
type WatermarkCallback = (jobId: string, fd: number) => void
```

Callback type used to register an event listener for forcible watermark processing.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-type WatermarkCallback = (jobId: string, fd: int) => void--><!--Device-print-type WatermarkCallback = (jobId: string, fd: int) => void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| fd | number | Yes | File descriptor of the file. |
