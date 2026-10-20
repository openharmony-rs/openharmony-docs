# configure

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## configure

```TypeScript
function configure(config: ConfigOption): void
```

Configures the application event logging function, such as setting the logging switch and directory storage quota.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-hiAppEvent-function configure(config: ConfigOption): void--><!--Device-hiAppEvent-function configure(config: ConfigOption): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ConfigOption](arkts-performanceanalysis-hiappevent-configoption-i.md) | Yes | Configuration items for application event logging. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11103001](../errorcode-hiappevent.md#11103001-invalid-maximum-storage-quota) | Invalid max storage quota value. Possibly caused by incorrectly formatted. |

**Examples**

```TypeScript
// Disable the event logging function.
let config1: hiAppEvent.ConfigOption = {
  disable: true,
};
hiAppEvent.configure(config1);

// Set the maximum size of the file storage directory to 100 MB.
let config2: hiAppEvent.ConfigOption = {
  maxStorage: '100MB',
};
hiAppEvent.configure(config2);
```
