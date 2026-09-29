# IndicatorComponentController

```TypeScript
declare class IndicatorComponentController
```

Provides methods for switching components.

**Since:** 15

<!--Device-unnamed-declare class IndicatorComponentController--><!--Device-unnamed-declare class IndicatorComponentController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(index: number, useAnimation?: boolean):void
```

Controlling IndicatorComponent to change to the specified subcomponent.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void--><!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | The index of item to be redirected. |
| useAnimation | boolean | No | If true, swipe to index item with animation. If false, swipe to index item without animation. The default value is false. |

## constructor

```TypeScript
constructor()
```

constructor.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-constructor()--><!--Device-IndicatorComponentController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showNext

```TypeScript
showNext():void
```

Called when the next child component is displayed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-showNext():void--><!--Device-IndicatorComponentController-showNext():void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showPrevious

```TypeScript
showPrevious():void
```

Called when the previous subcomponent is displayed.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-showPrevious():void--><!--Device-IndicatorComponentController-showPrevious():void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
