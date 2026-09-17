# PreviewConfiguration

Configures the style of the preview image during custom drag operations.

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delayCreating

```TypeScript
delayCreating?: boolean
```

Whether the preview builder is loaded at the time of setting.

The default value is **false**. The value **true** means that the preview builder is loaded at the time of setting, and **false** means the opposite.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onlyForLifting

```TypeScript
onlyForLifting?: boolean
```

Whether the custom preview image is used only for lifting.

**NOTE:** 

The default value is **false**. **true**: The custom preview image is used only for lifting. **false**: The custom preview image is used for both lifting and dragging. When the value is set to **true**, the preview image is used only during the lifting phase of a long press. For the preview image used during the dragging phase: The [dragPreview](arkts-arkui-commonmethod-c.md#dragpreview) attribute is ignored, and the system prioritizes the image returned in [onDragStart](arkts-arkui-commonmethod-c.md#ondragstart); if no image is returned in **onDragStart**, the component's snapshot is used.

**Type:** boolean

**Default:** false

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
