# DragInfo

Defines the attributes required for initiating a drag action and information carried in the dragging process.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## autoHideComponentUniqueIds

```TypeScript
autoHideComponentUniqueIds?: number | number[]
```

Unique ID of the component that is automatically hidden by the system during proactive dragging. A single unique ID or an array of unique IDs can be passed.

After the proactive dragging is successfully initiated, the system automatically hides the target component before displaying the drag preview window.

If the proactive dragging source also needs to be hidden, its unique ID must be passed as well.

The unique ID of a component can be obtained by using [UIContext.getFrameNodeById()](arkts-arkui-arkui-uicontext-uicontext-c.md#getframenodebyid) together with [FrameNode.getUniqueId()](arkts-arkui-framenode-c.md#getuniqueid).

You need to restore the component display status as required in the drag end callback.

**Type:** number &#124; number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data?: unifiedDataChannel.UnifiedData
```

Data carried in the dragging process.

The default value is null.

**Type:** [unifiedDataChannel.UnifiedData](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-unifieddata-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dataLoadParams

```TypeScript
dataLoadParams?: unifiedDataChannel.DataLoadParams
```

Parameters for deferred data loading from the drag source. This API provides data loading parameters to the system instead of directly providing complete data objects. When the user drops data on the target application, the system will use these parameters to request the actual data from the drag source. If set together with **data**, **dataLoadParams** takes effect.

The default value is null.

**Type:** [unifiedDataChannel.DataLoadParams](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-dataloadparams-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams?: string
```

Additional information about the drag action. Not supported currently.

The default value is null.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pointerId

```TypeScript
pointerId: number
```

ID of the touch point on the screen when dragging is started. The value is an integer in the [0, 9] range.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## previewOptions

```TypeScript
previewOptions?: DragPreviewOptions
```

Processing mode of the drag preview and the display of the number badge during dragging.

**Type:** [DragPreviewOptions](../arkts-components/arkts-arkui-dragpreviewoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## touchPoint

```TypeScript
touchPoint?: TouchPoint
```

Coordinates of the touch point. If this parameter is not set, the touch point is centered horizontally and shifted downward by 20% from the top.

**Type:** [TouchPoint](arkts-arkui-touchpoint-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
