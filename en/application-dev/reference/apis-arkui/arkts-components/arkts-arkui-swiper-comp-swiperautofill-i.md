# SwiperAutoFill

```TypeScript
declare interface SwiperAutoFill
```

Describes the auto-fill attribute.

**Since:** 10

<!--Device-unnamed-declare interface SwiperAutoFill--><!--Device-unnamed-declare interface SwiperAutoFill-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minSize

```TypeScript
minSize: VP
```

Minimum width for displaying elements, which is used to automatically calculate and change the display count of elements on one page based on the current width of **Swiper** and the **minSize** value. When the display count of elements on one page needs to be adaptively adjusted based on the width of the **Swiper** component, you are advised to set this parameter to achieve a better responsive layout effect.

Default value: **0**

Value range: (0, +∞). When the value is set to less than or equal to 0, **Swiper** displays one column.

**Type:** VP

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAutoFill-minSize: VP--><!--Device-SwiperAutoFill-minSize: VP-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
