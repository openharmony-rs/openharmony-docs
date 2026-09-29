# SpringLoadingDragInfos

```TypeScript
interface SpringLoadingDragInfos
```

Defines the drag event information when hover detection is triggered. This API provides drag data summaries and additional drag event information, allowing applications to decide whether to respond to hover detection callbacks.

**Since:** 20

<!--Device-dragController-interface SpringLoadingDragInfos--><!--Device-dragController-interface SpringLoadingDragInfos-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## dataSummary

```TypeScript
dataSummary?: unifiedDataChannel.Summary
```

Summary of the dragged data. The default value is null.

**Type:** [unifiedDataChannel.Summary](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-summary-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SpringLoadingDragInfos-dataSummary?: unifiedDataChannel.Summary--><!--Device-SpringLoadingDragInfos-dataSummary?: unifiedDataChannel.Summary-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraInfos

```TypeScript
extraInfos?: string
```

Additional information about the drag event. The default value is an empty string.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SpringLoadingDragInfos-extraInfos?: string--><!--Device-SpringLoadingDragInfos-extraInfos?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
