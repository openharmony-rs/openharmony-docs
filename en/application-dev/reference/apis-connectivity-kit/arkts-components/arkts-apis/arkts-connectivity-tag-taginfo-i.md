# TagInfo

Before a card with tags is read or written, **[TagInfo](arkts-connectivity-tag-taginfo-i.md)** must be obtained to determine the tag technologies supported by the card. In this way, the application can invoke the correct API to communicate with the card.

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Tag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## supportedProfiles

```TypeScript
supportedProfiles: number[]
```

Supported profiles.

Note: This parameter is supported since API version 7 and deprecated since API version 9. Use **[tag.TagInfo#technology](arkts-connectivity-tag-taginfo-i.md)** instead.

**Type:** number[]

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [technology](#technology)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.NFC.Tag

## technology

```TypeScript
technology: number[]
```

Supported tag technologies. Each number is a constant indicating the supported technology.

**Type:** number[]

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

## uid

```TypeScript
uid: number[]
```

Tag unique identifier (UID), which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Required permissions:** ohos.permission.NFC_TAG

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag
