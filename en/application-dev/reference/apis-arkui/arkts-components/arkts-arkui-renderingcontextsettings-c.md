# RenderingContextSettings

Configures the settings of a **CanvasRenderingContext2D** object, including whether to enable anti-aliasing.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(antialias?: boolean)
```

Constructs a **CanvasRenderingContext2D** object. Anti-aliasing can be enabled.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| antialias | boolean | No | Whether to enable anti-aliasing.<br>A value of **undefined** is treated as the default value. <br>**false**: Disable anti-aliasing. **true**: Enable anti-aliasing. <br>Default value: **false** <br>**NOTE:** <br> Anti-aliasing is enabled by default for text drawing. The **antialias** attribute of **RenderingContextSettings** does not affect the anti-aliasing effect of the drawn text. |

## antialias

```TypeScript
antialias?: boolean
```

Indicates whether anti-aliasing is enabled for canvas. <br>A value of **undefined** is treated as the default value. <br>**false**: Disable anti-aliasing. **true**: Enable anti-aliasing. <br>Default value: **false** <br>**NOTE:** <br> Anti-aliasing is enabled by default for text drawing. The **antialias** attribute of **RenderingContextSettings** does not affect the anti-aliasing effect of the drawn text. To adjust the anti-aliasing effect for text, use the [antialias](#antialias) API.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
