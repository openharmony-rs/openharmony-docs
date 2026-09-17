# NormalizerMode

Enumerates text normalization modes.

**Since:** 10

**System capability:** SystemCapability.Global.I18n

## NFC

```TypeScript
NFC = 1
```

Normalization form C, characters are decomposed and then re-composed by canonical equivalence

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## NFD

```TypeScript
NFD = 2
```

Normalization form D, characters are decomposed by canonical equivalence

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## NFKC

```TypeScript
NFKC = 3
```

Normalization form KC, characters are decomposed by compatibility, then re-composed by canonical equivalence

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## NFKD

```TypeScript
NFKD = 4
```

Normalization form KD, characters are decomposed by compatibility

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
