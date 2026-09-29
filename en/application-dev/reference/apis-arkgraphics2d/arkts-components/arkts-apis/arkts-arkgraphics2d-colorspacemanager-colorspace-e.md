# ColorSpace

```TypeScript
enum ColorSpace
```

Enumerates the color space types.

**Since:** 9

<!--Device-colorSpaceManager-enum ColorSpace--><!--Device-colorSpaceManager-enum ColorSpace-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-UNKNOWN = 0--><!--Device-ColorSpace-UNKNOWN = 0-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## ADOBE_RGB_1998

```TypeScript
ADOBE_RGB_1998 = 1
```

Adobe RGB (1998).

The conversion function is of the Adobe RGB (1998) type.

The encoding range is of the Full type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-ADOBE_RGB_1998 = 1--><!--Device-ColorSpace-ADOBE_RGB_1998 = 1-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DCI_P3

```TypeScript
DCI_P3 = 2
```

DCI-P3.

The conversion function is of the Gamma 2.6 type.

The encoding range is of the Full type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DCI_P3 = 2--><!--Device-ColorSpace-DCI_P3 = 2-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3

```TypeScript
DISPLAY_P3 = 3
```

Display P3.

The conversion function is of the SRGB type.

The encoding range is of the Full type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_P3 = 3--><!--Device-ColorSpace-DISPLAY_P3 = 3-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## SRGB

```TypeScript
SRGB = 4
```

SRGB.

The conversion function is of the SRGB type.

The encoding range is of the Full type.

This is the default color space type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-SRGB = 4--><!--Device-ColorSpace-SRGB = 4-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT709

```TypeScript
BT709 = 6
```

BT709.

The conversion function is of the BT709 type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT709 = 6--><!--Device-ColorSpace-BT709 = 6-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_EBU

```TypeScript
BT601_EBU = 7
```

BT601_P.

The conversion function is of the BT709 type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT601_EBU = 7--><!--Device-ColorSpace-BT601_EBU = 7-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_SMPTE_C

```TypeScript
BT601_SMPTE_C = 8
```

BT601_N.

The conversion function is of the BT709 type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT601_SMPTE_C = 8--><!--Device-ColorSpace-BT601_SMPTE_C = 8-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_HLG

```TypeScript
BT2020_HLG = 9
```

BT2020.

The conversion function is of the HLG type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT2020_HLG = 9--><!--Device-ColorSpace-BT2020_HLG = 9-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_PQ

```TypeScript
BT2020_PQ = 10
```

BT2020.

The conversion function is of the PQ type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT2020_PQ = 10--><!--Device-ColorSpace-BT2020_PQ = 10-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_HLG

```TypeScript
P3_HLG = 11
```

Display P3.

The conversion function is of the HLG type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-P3_HLG = 11--><!--Device-ColorSpace-P3_HLG = 11-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_PQ

```TypeScript
P3_PQ = 12
```

Display P3.

The conversion function is of the PQ type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-P3_PQ = 12--><!--Device-ColorSpace-P3_PQ = 12-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## ADOBE_RGB_1998_LIMIT

```TypeScript
ADOBE_RGB_1998_LIMIT = 13
```

Adobe RGB (1998).

The conversion function is of the Adobe RGB (1998) type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-ADOBE_RGB_1998_LIMIT = 13--><!--Device-ColorSpace-ADOBE_RGB_1998_LIMIT = 13-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_LIMIT

```TypeScript
DISPLAY_P3_LIMIT = 14
```

Display P3.

The conversion function is of the SRGB type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_P3_LIMIT = 14--><!--Device-ColorSpace-DISPLAY_P3_LIMIT = 14-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## SRGB_LIMIT

```TypeScript
SRGB_LIMIT = 15
```

SRGB.

The conversion function is of the SRGB type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-SRGB_LIMIT = 15--><!--Device-ColorSpace-SRGB_LIMIT = 15-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT709_LIMIT

```TypeScript
BT709_LIMIT = 16
```

BT709.

The conversion function is of the BT709 type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT709_LIMIT = 16--><!--Device-ColorSpace-BT709_LIMIT = 16-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_EBU_LIMIT

```TypeScript
BT601_EBU_LIMIT = 17
```

BT601_P.

The conversion function is of the BT709 type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT601_EBU_LIMIT = 17--><!--Device-ColorSpace-BT601_EBU_LIMIT = 17-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT601_SMPTE_C_LIMIT

```TypeScript
BT601_SMPTE_C_LIMIT = 18
```

BT601_N.

The conversion function is of the BT709 type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT601_SMPTE_C_LIMIT = 18--><!--Device-ColorSpace-BT601_SMPTE_C_LIMIT = 18-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_HLG_LIMIT

```TypeScript
BT2020_HLG_LIMIT = 19
```

BT2020.

The conversion function is of the HLG type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT2020_HLG_LIMIT = 19--><!--Device-ColorSpace-BT2020_HLG_LIMIT = 19-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## BT2020_PQ_LIMIT

```TypeScript
BT2020_PQ_LIMIT = 20
```

BT2020.

The conversion function is of the PQ type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-BT2020_PQ_LIMIT = 20--><!--Device-ColorSpace-BT2020_PQ_LIMIT = 20-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_HLG_LIMIT

```TypeScript
P3_HLG_LIMIT = 21
```

Display P3.

The conversion function is of the HLG type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-P3_HLG_LIMIT = 21--><!--Device-ColorSpace-P3_HLG_LIMIT = 21-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## P3_PQ_LIMIT

```TypeScript
P3_PQ_LIMIT = 22
```

Display P3.

The conversion function is of the PQ type.

The encoding range is of the Limit type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-P3_PQ_LIMIT = 22--><!--Device-ColorSpace-P3_PQ_LIMIT = 22-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_P3

```TypeScript
LINEAR_P3 = 23
```

Display P3.

The conversion function is of the Linear type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-LINEAR_P3 = 23--><!--Device-ColorSpace-LINEAR_P3 = 23-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_SRGB

```TypeScript
LINEAR_SRGB = 24
```

SRGB.

The conversion function is of the Linear type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-LINEAR_SRGB = 24--><!--Device-ColorSpace-LINEAR_SRGB = 24-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_BT709

```TypeScript
LINEAR_BT709 = LINEAR_SRGB
```

Same as that of LINEAR_SRGB.

BT709.

The conversion function is of the Linear type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-LINEAR_BT709 = LINEAR_SRGB--><!--Device-ColorSpace-LINEAR_BT709 = LINEAR_SRGB-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## LINEAR_BT2020

```TypeScript
LINEAR_BT2020 = 25
```

BT2020.

The conversion function is of the Linear type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-LINEAR_BT2020 = 25--><!--Device-ColorSpace-LINEAR_BT2020 = 25-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_SRGB

```TypeScript
DISPLAY_SRGB = SRGB
```

Same as that of SRGB.

SRGB.

The conversion function is of the SRGB type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_SRGB = SRGB--><!--Device-ColorSpace-DISPLAY_SRGB = SRGB-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_SRGB

```TypeScript
DISPLAY_P3_SRGB = DISPLAY_P3
```

Same as that of DISPLAY_P3.

Display P3.

The conversion function is of the SRGB type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_P3_SRGB = DISPLAY_P3--><!--Device-ColorSpace-DISPLAY_P3_SRGB = DISPLAY_P3-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_HLG

```TypeScript
DISPLAY_P3_HLG = P3_HLG
```

Same as that of P3_HLG.

Display P3.

The conversion function is of the HLG type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_P3_HLG = P3_HLG--><!--Device-ColorSpace-DISPLAY_P3_HLG = P3_HLG-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_P3_PQ

```TypeScript
DISPLAY_P3_PQ = P3_PQ
```

Same as that of P3_PQ.

Display P3.

The conversion function is of the PQ type.

The encoding range is of the Full type.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-DISPLAY_P3_PQ = P3_PQ--><!--Device-ColorSpace-DISPLAY_P3_PQ = P3_PQ-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## H_LOG

```TypeScript
H_LOG = 26
```

BT2020.

The conversion function is of the LOG type.

**Since:** 18

<!--Device-ColorSpace-H_LOG = 26--><!--Device-ColorSpace-H_LOG = 26-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## DISPLAY_BT2020_SRGB

```TypeScript
DISPLAY_BT2020_SRGB = 27
```

DISPLAY BT2020.

The conversion function is of the SRGB type.

The encoding range is of the Full type.

**Since:** 20

<!--Device-ColorSpace-DISPLAY_BT2020_SRGB = 27--><!--Device-ColorSpace-DISPLAY_BT2020_SRGB = 27-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## CUSTOM

```TypeScript
CUSTOM = 5
```

Custom type.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ColorSpace-CUSTOM = 5--><!--Device-ColorSpace-CUSTOM = 5-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.ColorManager.Core
