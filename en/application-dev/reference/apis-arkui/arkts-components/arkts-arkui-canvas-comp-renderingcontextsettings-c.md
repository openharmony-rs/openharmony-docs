# RenderingContextSettings

```TypeScript
declare class RenderingContextSettings
```

Configures the settings of a **CanvasRenderingContext2D** object, including whether to enable anti-aliasing.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(antialias?: boolean)
```

Creates a **RenderingContextSettings** object, with support for configuring anti-aliasing.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| antialias | boolean | No | Whether to enable anti-aliasing for the canvas. <br>Abnormal values **undefined** or **null** are processed as the default value. <br>**true**: anti-aliasing is enabled; **false**: anti-aliasing is disabled. <br>Default value: **false** <br>**NOTE:** <br> Anti-aliasing is enabled by default for text drawing. The **antialias** attribute of **RenderingContextSettings** does not affect the anti-aliasing effect of text drawing. To modify the text anti-aliasing effect, use the [antialias&lt;sup&gt;24+&lt;/sup&gt;](#antialias) API. |

## antialias

```TypeScript
antialias?: boolean
```

Whether to enable anti-aliasing for the canvas. <br>Abnormal values **undefined** or **null** are processed as the default value. <br>**true**: anti-aliasing is enabled; **false**: anti-aliasing is disabled. <br>Default value: **false** <br>**NOTE:** <br> Anti-aliasing is enabled by default for text drawing. The **antialias** attribute of **RenderingContextSettings** does not affect the anti-aliasing effect of text drawing. To modify the text anti-aliasing effect, use the [antialias&lt;sup&gt;24+&lt;/sup&gt;](#antialias) API.

**Type:** boolean

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
