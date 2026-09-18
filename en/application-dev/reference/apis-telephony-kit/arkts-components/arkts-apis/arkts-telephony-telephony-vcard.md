# @ohos.telephony.vcard(VCard)

VCard is a file format standard for electronic business cards. It contains information such as names, addresses, phone numbers, URLs, logos, and photos. The VCard module provides the VCard management functions, including importing VCard files to the contact database and exporting contact data to VCard files.

**Since:** 11

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | Exports contacts as a vcard file (VCF). This API uses an asynchronous callback to return the result. |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | Exports contacts as a vcard file (VCF). This API uses a promise to return the result. |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | Exports contacts as a vcard file (VCF). This API uses an asynchronous callback to return the result. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses a promise to return the result. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [VCardBuilderOptions](arkts-telephony-vcard-vcardbuilderoptions-i.md) | Defines the VCard information. |

### Enums

| Name | Description |
| --- | --- |
| [VCardType](arkts-telephony-vcard-vcardtype-e.md) | Enumerates VCard versions. |
