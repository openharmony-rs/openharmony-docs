# Font

```TypeScript
declare interface Font
```

Sets the text style.

> **NOTE:** 
> 
> You can use [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) to register custom fonts.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## family

```TypeScript
family?: string | Resource
```

Font family. Default font: **'HarmonyOS Sans'**.

To specify multiple fonts, separate them with commas (,), and fonts are applied in priority order. Example: **'Arial, HarmonyOS Sans'**.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

Font size. If the value is of the number type, the unit fp is used. Percentage strings are not supported.

Default value: **16.0**

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: FontStyle
```

Font style.

Default value: **FontStyle.Normal**

**Type:** [FontStyle](arkts-arkui-fontstyle-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight?: FontWeight | number | string
```

Font weight. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a thicker font.

Default value: **400** | **FontWeight.Normal**

**Type:** [FontWeight](arkts-arkui-fontweight-e.md) &#124; number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
