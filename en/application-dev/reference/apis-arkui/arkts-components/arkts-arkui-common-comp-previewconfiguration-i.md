# PreviewConfiguration

```TypeScript
declare interface PreviewConfiguration
```

Configures the style of the preview image during custom drag operations.

**Since:** 15

<!--Device-unnamed-declare interface PreviewConfiguration--><!--Device-unnamed-declare interface PreviewConfiguration-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delayCreating

```TypeScript
delayCreating?: boolean
```

Whether the component preview builder is created with a delay.

The default value is **false**. The value **true** means that the component preview builder is created only when the drag preview needs to be generated, and **false** means that the component preview builder is created when it is set.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-PreviewConfiguration-delayCreating?: boolean--><!--Device-PreviewConfiguration-delayCreating?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onlyForLifting

```TypeScript
onlyForLifting?: boolean
```

Whether the custom preview image is used only for lifting.

**NOTE:** 

The default value is **false**. **true**: The custom preview image is used only for lifting. **false**: The custom preview image is used for both lifting and dragging. When the value is set to **true**, the preview image is used only during the lifting phase of a long press. For the preview image used during the dragging phase: The [dragPreview](arkts-arkui-common-comp-commonmethod-c.md#dragpreview1) attribute is ignored, and the system prioritizes the image returned in [onDragStart](arkts-arkui-common-comp-commonmethod-c.md#ondragstart); if no image is returned in **onDragStart**, the component's snapshot is used.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-PreviewConfiguration-onlyForLifting?: boolean--><!--Device-PreviewConfiguration-onlyForLifting?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
