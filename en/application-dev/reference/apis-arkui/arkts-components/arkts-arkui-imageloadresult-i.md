# ImageLoadResult

Describes the object returned after the callback is triggered when an image is successfully loaded or decoded.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## componentHeight

```TypeScript
componentHeight: number
```

Height of the component.

Unit: px

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## componentWidth

```TypeScript
componentWidth: number
```

Width of the component.

Unit: px

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentHeight

```TypeScript
contentHeight: number
```

Actual rendered height of the image.

Unit: px

**NOTE:** 

This parameter is valid only when the return value of **loadingStatus** is **1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentOffsetX

```TypeScript
contentOffsetX: number
```

Offset of the rendered content relative to the component on the x-axis.

Unit: px

**NOTE:** 

This parameter is valid only when the return value of **loadingStatus** is **1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentOffsetY

```TypeScript
contentOffsetY: number
```

Offset of the rendered content relative to the component on the y-axis

Unit: px

**NOTE:** 

This parameter is valid only when the return value of **loadingStatus** is **1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentWidth

```TypeScript
contentWidth: number
```

Actual rendered width of the image.

Unit: px

**NOTE:** 

This parameter is valid only when the return value of **loadingStatus** is **1**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height: number
```

Height of the image.

Unit: px

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loadingStatus

```TypeScript
loadingStatus: number
```

Loading status of the image.

**NOTE:** 

If the return value is **0**, the image is successfully loaded. If the return value is **1**, the image is successfully decoded.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

Width of the image.

Unit: px

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
