# TouchResult

```TypeScript
declare class TouchResult
```

Defines the custom event dispatch result. You can influence event dispatch by returning specific results.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id?: string
```

Unique ID of the child component.

If **strategy** is set to **TouchTestStrategy.DEFAULT**, **id** is optional. If **strategy** is set to **TouchTestStrategy.FORWARD_COMPETITION** or **TouchTestStrategy.FORWARD**, **id** is mandatory. If **id** is not returned, the strategy **TouchTestStrategy.DEFAULT** is used.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strategy

```TypeScript
strategy: TouchTestStrategy
```

Event dispatch strategy.

**Type:** [TouchTestStrategy](arkts-arkui-common-comp-touchteststrategy-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
