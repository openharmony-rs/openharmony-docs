# ProgressIndicator

```TypeScript
enum ProgressIndicator
```

Enumerates the progress indicator options, which determine whether to use the system default progress display.

**Since:** 15

<!--Device-unifiedDataChannel-enum ProgressIndicator--><!--Device-unifiedDataChannel-enum ProgressIndicator-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DEFAULT

```TypeScript
DEFAULT = 1
```

Uses the system default progress display. If data is obtained within 500 ms, the default progress bar will not be displayed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ProgressIndicator-DEFAULT = 1--><!--Device-ProgressIndicator-DEFAULT = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## NONE

```TypeScript
NONE = 0
```

Does not use the system default progress display.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ProgressIndicator-NONE = 0--><!--Device-ProgressIndicator-NONE = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
