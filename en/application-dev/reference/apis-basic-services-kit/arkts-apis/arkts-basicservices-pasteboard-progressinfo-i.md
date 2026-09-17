# ProgressInfo

Defines the progress information. This information is reported only when [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) is set to **NONE**.

**Since:** 15

**System capability:** SystemCapability.MiscServices.Pasteboard

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## progress

```TypeScript
progress: number
```

If the progress indicator provided by the system is not used, the system reports the progress percentage of the paste task.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.MiscServices.Pasteboard
