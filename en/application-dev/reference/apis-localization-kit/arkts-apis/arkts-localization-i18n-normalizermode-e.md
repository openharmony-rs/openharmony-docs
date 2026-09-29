# NormalizerMode

```TypeScript
export enum NormalizerMode
```

Enumerates text normalization modes.

**Since:** 10

<!--Device-i18n-export enum NormalizerMode--><!--Device-i18n-export enum NormalizerMode-End-->

**System capability:** SystemCapability.Global.I18n

## NFC

```TypeScript
NFC = 1
```

Normalization form C, characters are decomposed and then re-composed by canonical equivalence

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NormalizerMode-NFC = 1--><!--Device-NormalizerMode-NFC = 1-End-->

**System capability:** SystemCapability.Global.I18n

## NFD

```TypeScript
NFD = 2
```

Normalization form D, characters are decomposed by canonical equivalence

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NormalizerMode-NFD = 2--><!--Device-NormalizerMode-NFD = 2-End-->

**System capability:** SystemCapability.Global.I18n

## NFKC

```TypeScript
NFKC = 3
```

Normalization form KC, characters are decomposed by compatibility, then re-composed by canonical equivalence

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NormalizerMode-NFKC = 3--><!--Device-NormalizerMode-NFKC = 3-End-->

**System capability:** SystemCapability.Global.I18n

## NFKD

```TypeScript
NFKD = 4
```

Normalization form KD, characters are decomposed by compatibility

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NormalizerMode-NFKD = 4--><!--Device-NormalizerMode-NFKD = 4-End-->

**System capability:** SystemCapability.Global.I18n
