# IndicatorComponentController

```TypeScript
declare class IndicatorComponentController
```

Controller of the **Indicator** component. You can bind this object to the **Indicator** component to control page turning. By passing the same **IndicatorComponentController** instance to the constructor of the **IndicatorComponent** and the **indicator** attribute of the **Swiper** component, you can bind the **Indicator** and **Swiper** components for linkage.

**Since:** 15

<!--Device-unnamed-declare class IndicatorComponentController--><!--Device-unnamed-declare class IndicatorComponentController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(index: number, useAnimation?: boolean):void
```

Navigates to the specified indicator. Before using this method, ensure that the controller has been bound to the **Indicator** component. This is applicable to scenarios where you need to jump to a specified indicator.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void--><!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index value of the specified indicator.<br>**Note:** <br>If the set value is less than 0 or greater than the maximum indicator index, 0 is used. |
| useAnimation | boolean | No | Whether to use an animation for when the target index is reached. The value **true** means to use an animation, and **false** means the opposite.<br>Default value: **false**. |

## constructor

```TypeScript
constructor()
```

A constructor used to create an **IndicatorComponentController** object.

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

Moves to the next indicator. When bound to a **Swiper** component, it also controls the **Swiper** to switch to the next page. This is applicable to scenarios where the indicator switching is controlled through buttons or other interaction methods.

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

Moves to the previous indicator. When bound to a **Swiper** component, it also controls the **Swiper** to switch to the previous page. This is applicable to scenarios where the indicator switching is controlled through buttons or other interaction methods.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-IndicatorComponentController-showPrevious():void--><!--Device-IndicatorComponentController-showPrevious():void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
