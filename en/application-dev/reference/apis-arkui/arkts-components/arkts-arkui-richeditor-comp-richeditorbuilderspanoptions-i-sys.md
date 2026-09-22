# RichEditorBuilderSpanOptions

```TypeScript
declare interface RichEditorBuilderSpanOptions
```

Sets the offset position and style of the inserted builder.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dragBackgroundColor

```TypeScript
dragBackgroundColor? : ColorMetrics
```

Sets the background color of the backboard when a BuilderSpan is dragged individually. If this parameter is not configured or an invalid color value is passed, the default value is used.

Default value: the drag backboard color that follows the system theme.

**Type:** ColorMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isDragShadowNeeded

```TypeScript
isDragShadowNeeded?: boolean
```

Sets whether a shadow is needed when a BuilderSpan is dragged individually. The value **true** means that a shadow is needed, and **false** means that a shadow is not needed. If this parameter is not configured or an invalid value is passed, the default value is used.

Default value: **true**.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
