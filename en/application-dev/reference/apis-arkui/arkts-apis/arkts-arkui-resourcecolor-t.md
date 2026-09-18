# ResourceColor

```TypeScript
declare type ResourceColor = Color | number | string | Resource
```

Defines the color types of resources.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| [Color](arkts-arkui-color-e.md) | Color enums. |
| number | Color in HEX format. RGB and ARGB are supported. Examples: **0xffffff** and **0xffff0000**. The input length is not checked; the format is determined by the value range. For example, **0x00ffffff** is parsed as RGB. |
| string | Color in RGB, RGBA, or ARGB format.<br>RGB examples: **'#ffffff'** and **'rgb(255, 100, 255)'** <br>RGBA example: **'rgba(255, 100, 255, 0.5)'** <br>ARGB example: **'#ff000000'** |
| [Resource](arkts-arkui-resource-t.md) | Color referenced from system or app resources. |
