# NdefRecord

Defines an NDEF record. For details, see *NFCForum-TS-NDEF_1.0*.

**Since:** 9

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

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

## payload

```TypeScript
payload: number[]
```

NDEF payload, which consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

## rtdType

```TypeScript
rtdType: number[]
```

Record type definition (RTD) of the NDEF record. It consists of hexadecimal numbers ranging from **0x00** to **0xFF**.

**Type:** number[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

## tnf

```TypeScript
tnf: number
```

Type name field (TNF) of the NDEF record.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag
