# @ohos.telephony.vcard(VCard)

VCard is a file format standard for electronic business cards. It contains information such as names, addresses, phone numbers, URLs, logos, and photos. The VCard module provides the VCard management functions, including importing VCard files to the contact database and exporting contact data to VCard files.

**Since:** 11

<!--Device-unnamed-declare namespace vcard--><!--Device-unnamed-declare namespace vcard-End-->

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md#exportvcard-1) | Export contacts to a VCF (VCard file) file. This mode is applicable to scenarios such as contact data backup, cross-device contact migration, and contact sharing through files. Use the callback asynchronous callback. |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md#exportvcard-2) | Export contacts to a VCF (VCard file) file. This mode is applicable to scenarios such as contact data backup, cross-device contact migration, and contact sharing through files. Use Promise asynchronous callbacks. |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md#exportvcard-3) | Export contacts to a VCF (VCard file) file. This mode is applicable to scenarios such as contact data backup, cross-device contact migration, and contact sharing through files. Use the callback asynchronous callback. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md#importvcard-1) | Import the VCard file into the contact database. Applies to scenarios such as importing contacts in batches and restoring contact data after receiving VCard files from other devices or applications. Use the callback asynchronous callback. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md#importvcard-2) | Import the VCard file into the contact database. Applies to scenarios such as importing contacts in batches and restoring contact data after receiving VCard files from other devices or applications. Use Promise asynchronous callbacks. |
| [importVCard](arkts-telephony-vcard-importvcard-f.md#importvcard-3) | Import the VCard file into the contact database. Applies to scenarios such as importing contacts in batches and restoring contact data after receiving VCard files from other devices or applications. Use the callback asynchronous callback. |

### Interfaces

| Name | Description |
| --- | --- |
| [VCardBuilderOptions](arkts-telephony-vcard-vcardbuilderoptions-i.md) | Defines the VCard information. |

### Enums

| Name | Description |
| --- | --- |
| [VCardType](arkts-telephony-vcard-vcardtype-e.md) | Enumerates VCard versions. |
