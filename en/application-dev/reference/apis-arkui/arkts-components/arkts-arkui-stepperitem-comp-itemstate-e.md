# ItemState

```TypeScript
declare enum ItemState
```

Display status of **nextLabel** in the stepper.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** Swiper

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

The button on the right is clickable and can navigate users to the next **StepperItem** when it is clicked.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 22. You are advised to use [index](arkts-arkui-swiper-comp-attribute.md#index) instead.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** index

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Disabled

```TypeScript
Disabled
```

The button on the right is disabled.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 22. You are advised to use [indicatorInteractive](arkts-arkui-swiper-comp-attribute.md#indicatorinteractive) instead.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** [indicatorInteractive](arkts-arkui-swiper-comp-attribute.md#indicatorinteractive)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Waiting

```TypeScript
Waiting
```

The button on the right is not displayed, and a progress bar is displayed instead.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 22. You are advised to use Swiper instead.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** Swiper

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Skip

```TypeScript
Skip
```

The button on the right reads "Skip" by default. You can define the processing logic for this state in the **onSkip** callback of the stepper.

**NOTE:** 

This API is supported since API version 8 and deprecated since API version 22. You are advised to use [index](arkts-arkui-swiper-comp-attribute.md#index) instead.

**Since:** 8

**Deprecated since:** 22

**Substitutes:** index

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
