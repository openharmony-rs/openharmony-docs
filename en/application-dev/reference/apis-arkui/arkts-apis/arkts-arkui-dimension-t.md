# Dimension

```TypeScript
declare type Dimension = PX | VP | FP | LPX | Percentage | Resource
```

Defines a size unit.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| [PX](arkts-arkui-px-t.md) | Physical pixel unit type. The unit px must be included, for example, **'10px'**. |
| [VP](arkts-arkui-vp-t.md) | Viewport pixel unit. The unit vp can be included or omitted, for example, **10** or **'10vp'**. |
| [FP](arkts-arkui-fp-t.md) | Font pixel unit type. The unit fp must be included, for example, **'10fp'**. |
| [LPX](arkts-arkui-lpx-t.md) | Logical pixel unit type. The unit lpx must be included, for example, **'10lpx'**. |
| [Percentage](arkts-arkui-percentage-t.md) | Percentage type. The unit % must be included, for example, **'10%'**. |
| [Resource](arkts-arkui-resource-t.md) | Size referenced from system or app resources. |
