# NdefRecord

```TypeScript
export interface NdefRecord
```

Defines an NDEF record. For details, see *NFCForum-TS-NDEF_1.0*.

**Since:** 9

<!--Device-tag-export interface NdefRecord--><!--Device-tag-export interface NdefRecord-End-->

**System capability:** SystemCapability.Communication.NFC.Tag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## id

```TypeScript
id: number[]
```

NDEF record ID, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NdefRecord-id: int[]--><!--Device-NdefRecord-id: int[]-End-->

**System capability:** SystemCapability.Communication.NFC.Tag

## payload

```TypeScript
payload: number[]
```

NDEF payload, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NdefRecord-payload: int[]--><!--Device-NdefRecord-payload: int[]-End-->

**System capability:** SystemCapability.Communication.NFC.Tag

## rtdType

```TypeScript
rtdType: number[]
```

Record type definition (RTD) of the NDEF record. It consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NdefRecord-rtdType: int[]--><!--Device-NdefRecord-rtdType: int[]-End-->

**System capability:** SystemCapability.Communication.NFC.Tag

## tnf

```TypeScript
tnf: number
```

Type name field (TNF) of the NDEF record.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-NdefRecord-tnf: int--><!--Device-NdefRecord-tnf: int-End-->

**System capability:** SystemCapability.Communication.NFC.Tag
