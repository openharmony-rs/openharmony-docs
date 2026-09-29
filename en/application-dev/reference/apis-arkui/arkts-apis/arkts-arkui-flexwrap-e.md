# FlexWrap

```TypeScript
declare enum FlexWrap
```

Sets whether elements are arranged in a single row/column or multiple rows/columns in the **Flex** container.

**Since:** 7

<!--Device-unnamed-declare enum FlexWrap--><!--Device-unnamed-declare enum FlexWrap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NoWrap

```TypeScript
NoWrap
```

The child components in the flex container are arranged in a single line. If any of them have minimum size constraints applied, the flex container does not forcibly shrink them when overflow occurs.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-FlexWrap-NoWrap--><!--Device-FlexWrap-NoWrap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Wrap

```TypeScript
Wrap
```

The child components in the flex container are arranged in multiple lines, and they may overflow.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-FlexWrap-Wrap--><!--Device-FlexWrap-Wrap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WrapReverse

```TypeScript
WrapReverse
```

The child components in the flex container are reversely arranged in multiple lines, and they may overflow.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-FlexWrap-WrapReverse--><!--Device-FlexWrap-WrapReverse-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
