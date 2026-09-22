# PresetSplitRatio

```TypeScript
export declare enum PresetSplitRatio
```

Enumerates the split ratios.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAYOUT_1V1

```TypeScript
LAYOUT_1V1 = 1
```

1:1 ratio, indicating that the primary area and secondary area are equal in size. When used for **verticalSplitRatio**, the height ratio of the upper and lower areas is 1:1. When used for **horizontalSplitRatio**, the width ratio of the left and right areas is 1:1.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAYOUT_2V3

```TypeScript
LAYOUT_2V3 = 0.6666666666666666
```

2:3 ratio, indicating that the primary area is approximately 0.667 times (2/3) the size of the secondary area, that is, the primary area occupies 2/5 and the secondary area occupies 3/5. When used for **verticalSplitRatio**, the height ratio of the upper and lower areas is 2:3. When used for **horizontalSplitRatio**, the width ratio of the left and right areas is 2:3.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAYOUT_3V2

```TypeScript
LAYOUT_3V2 = 1.5
```

3:2 ratio, indicating that the primary area is 1.5 times the size of the secondary area, that is, the primary area occupies 3/5 and the secondary area occupies 2/5. When used for **verticalSplitRatio**, the height ratio of the upper and lower areas is 3:2. When used for **horizontalSplitRatio**, the width ratio of the left and right areas is 3:2.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
