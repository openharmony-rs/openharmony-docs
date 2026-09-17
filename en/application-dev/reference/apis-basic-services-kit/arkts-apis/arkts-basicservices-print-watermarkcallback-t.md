# WatermarkCallback

```TypeScript
type WatermarkCallback = (jobId: string, fd: number) => void
```

Defines the callback type used in registering to listen for watermark handling. The value of jobId indicates the print job ID. The value of fd indicates the fd.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | the print job ID<br>Print job ID in preview. |
| fd | number | Yes | File Descriptor<br>File descriptor in preview. |
