# setGlobalRetryOptions

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## setGlobalRetryOptions

```TypeScript
function setGlobalRetryOptions(options?: RetryOptions): void
```

Sets retry options for all tasks. Used when task-specific retry configuration is not configured.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RetryOptions](arkts-basicservices-cachedownload-retryoptions-i.md) | No | Task retry configurations.<br>Default value: Refer to the default value of RetryOptions. |

**Examples**

```TypeScript
try {
  // Set the maximum number of retries for a task globally.
  cacheDownload.setGlobalRetryOptions({
    maxRetryCount: 1
  });
  cacheDownload.download("https://www.example.com", {});
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err?.code}, err message: ${err?.message}`);
}
```
