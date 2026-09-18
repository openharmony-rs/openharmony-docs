# nfctech(Standard NFC Technologies)

The **nfctech** module provides APIs for reading and writing tags that use different Near-Field Communication (NFC)
 technologies.

> **NOTE**
 >
 > If an error is reported while importing the tag module editor, the capabilities of a specific device model may
 > exceed the capability set defined for the default device. To use these capabilities, configure a custom SysCap by
 > following instructions in
 > [SystemCapability](https://developer.huawei.com/consumer/en/doc/harmonyos-references/syscap).



## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BarcodeTag](arkts-connectivity-nfctech-barcodetag-i.md) | Provides the capability of reading barcode label attributes and accessing I/O operations. It is inherited from **TagSession**. |
| [IsoDepTag](arkts-connectivity-nfctech-isodeptag-i.md) | Provides APIs to access ISO-DEP (ISO 14443-4) properties and I/O operations on a tag. This class inherits from **TagSession**. |
| [MifareClassicTag](arkts-connectivity-nfctech-mifareclassictag-i.md) | Provides APIs to access MIFARE Classic properties and perform I/O operations on a tag. This class inherits from [TagSession](arkts-connectivity-tagsession-tagsession-i.md). |
| [MifareUltralightTag](arkts-connectivity-nfctech-mifareultralighttag-i.md) | Provides APIs to access MIFARE Ultralight properties and perform I/O operations on a tag. This class inherits from **TagSession**. |
| [NdefFormatableTag](arkts-connectivity-nfctech-ndefformatabletag-i.md) | Provides APIs for formatting NDEF formattable tags. This class inherits from **TagSession**. |
| [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | Provides methods for Message of NDEF. |
| [NdefTag](arkts-connectivity-nfctech-ndeftag-i.md) | Provides APIs to access the tags in the NFC Data Exchange Format (NDEF). This class inherits from **TagSession**. |
| [NfcATag](arkts-connectivity-nfctech-nfcatag-i.md) | Provides APIs to access NFC-A (ISO 14443-3A) properties and perform I/O operations on a tag. This class inherits from **[TagSession](arkts-connectivity-tagsession-tagsession-i.md)**. |
| [NfcBTag](arkts-connectivity-nfctech-nfcbtag-i.md) | Provides APIs to access NFC-B (ISO 14443-3B) properties and perform I/O operations on a tag. This class inherits from **TagSession**. |
| [NfcFTag](arkts-connectivity-nfctech-nfcftag-i.md) | Provides APIs to access NFC-F (JIS 6319-4) properties and perform I/O operations on a tag. This class inherits from **TagSession**. |
| [NfcVTag](arkts-connectivity-nfctech-nfcvtag-i.md) | Provides APIs to access NFC-V (ISO 15693) properties and perform I/O operations on a tag. This class inherits from **TagSession**. |
