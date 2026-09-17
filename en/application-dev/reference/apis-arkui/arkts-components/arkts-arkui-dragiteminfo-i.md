# DragItemInfo

Defines the information about the dragged item during drag.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Custom component to display during dragging. If **pixelMap** is set, this parameter is ignored.

**NOTE:** 

Global builder definition is not supported. If the Image component is used in the builder, enable synchronous loading whenever possible, that is, set the syncLoad attribute of the component to **true**. The builder is used only to generate the image displayed during the current dragging. Changes to the builder, if any, apply to the next dragging, but not to the current dragging.

When passing the builder as a parameter, the format builder: ()=&gt;{this.customBuilder()} is recommended to ensure correctness of this binding. For details, see [Using Functions Decorated with @Builder as CustomBuilder Types](../../../ui/state-management/arkts-builder.md#using-functions-decorated-with-builder-as-custombuilder-types).

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraInfo

```TypeScript
extraInfo?: string
```

Additional information about the dragged item, used to describe the item being dragged.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pixelMap

```TypeScript
pixelMap?: PixelMap
```

Image to be displayed during dragging.

**Type:** [PixelMap](arkts-arkui-pixelmap-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
