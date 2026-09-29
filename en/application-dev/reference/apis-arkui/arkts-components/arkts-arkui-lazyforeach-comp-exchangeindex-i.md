# ExchangeIndex

```TypeScript
interface ExchangeIndex
```

Defines position of exchange data.

**Since:** 12

<!--Device-unnamed-interface ExchangeIndex--><!--Device-unnamed-interface ExchangeIndex-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: number
```

Second swap position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExchangeIndex-end: number--><!--Device-ExchangeIndex-end: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: number
```

First swap position. The value range is [0, data source length - 1]. Rendering is abnormal when the value exceeds the value range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ExchangeIndex-start: number--><!--Device-ExchangeIndex-start: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
