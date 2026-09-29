# ProgressInfo

```TypeScript
interface ProgressInfo
```

Defines the progress information. This information is reported only when [ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md) is set to **NONE**.

**Since:** 15

<!--Device-pasteboard-interface ProgressInfo--><!--Device-pasteboard-interface ProgressInfo-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ProgressInfo-progress: int--><!--Device-ProgressInfo-progress: int-End-->

**System capability:** SystemCapability.MiscServices.Pasteboard
