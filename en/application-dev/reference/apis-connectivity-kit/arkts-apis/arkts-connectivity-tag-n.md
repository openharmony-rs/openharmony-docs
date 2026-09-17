# tag(Standard NFC Tags)

The **tag** module provides APIs for operating and managing NFC tags. The following tag read modes are available:

Background mode: The device reads the tag by using NFC without starting any application, and then searches for applications based on the tag type. If only one application is matched, the card reading page of that application will be started. If multiple applications are matched, an application selector will be started, asking the user to select an application. Background mode does not involve tag-related APIs. For details, see [nfc-tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md#accessing-an-nfc-tag-without-starting-an-application).

Foreground mode: A foreground application has priority to read the NFC tag discovered.

> **NOTE:** 
> 
> 2. Since API version 26.0.0, it is more accurate to determine whether a device supports NFC by calling both [canIUse("SystemCapability.Communication.NFC.Tag")](../../../reference/common/init.md#caniuse) and [nfcController.isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md). If the device does not support NFC, the application stability may be affected. For details, see [NFC Tag Read/Write Development](../../../connectivity/nfc/nfc-tag-access-guide.md).
> 
> 3. If an error is reported while importing the tag module editor, the capabilities of a specific device model may exceed the capability set defined for the default device. To use these capabilities, configure a custom SysCap by following instructions in [SystemCapability](https://developer.huawei.com/consumer/en/doc/harmonyos-references/syscap).

**Since:** 7

**System capability:** SystemCapability.Communication.NFC.Tag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [ndef](arkts-connectivity-tag-ndef-n.md) | Provides methods for accessing NDEF tag. |

### Functions

| Name | Description |
| --- | --- |
| [getNfcATag](arkts-connectivity-tag-getnfcatag-f.md) | Obtains an **NfcATag** object, which allows access to the tags that use the NFC-A technology. |
| [getNfcA](arkts-connectivity-tag-getnfca-f.md) | Obtains an **NfcATag** object, which allows access to the tags that use the NFC-A technology. |
| [getNfcBTag](arkts-connectivity-tag-getnfcbtag-f.md) | Obtains an **NfcBTag** object, which allows access to the tags that use the NFC-B technology. |
| [getNfcB](arkts-connectivity-tag-getnfcb-f.md) | Obtains an **NfcBTag** object, which allows access to the tags that use the NFC-B technology. |
| [getNfcFTag](arkts-connectivity-tag-getnfcftag-f.md) | Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology. |
| [getNfcF](arkts-connectivity-tag-getnfcf-f.md) | Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology. |
| [getNfcVTag](arkts-connectivity-tag-getnfcvtag-f.md) | Obtains an **NfcVTag** object, which allows access to the tags that use the NFC-V technology. |
| [getNfcV](arkts-connectivity-tag-getnfcv-f.md) | Obtains an **NfcVTag** object, which allows access to the tags that use the NFC-V technology. |
| [getIsoDep](arkts-connectivity-tag-getisodep-f.md) | Obtains an **IsoDepTag** object, which allows access to the tags that use the IsoDep technology. |
| [getNdef](arkts-connectivity-tag-getndef-f.md) | Obtains an **NdefTag** object, which allows access to NFC Data Exchange Format (NDEF) tags. |
| [getMifareClassic](arkts-connectivity-tag-getmifareclassic-f.md) | Obtains a **MifareClassicTag** object, which allows access to the tags that use MIFARE Classic. |
| [getMifareUltralight](arkts-connectivity-tag-getmifareultralight-f.md) | Obtains a **MifareUltralightTag** object, which allows access to the tags that use MIFARE Ultralight. |
| [getNdefFormatable](arkts-connectivity-tag-getndefformatable-f.md) | Obtains an **NdefFormatableTag** object, which allows access to the tags that are NDEF formattable. |
| [getTagInfo](arkts-connectivity-tag-gettaginfo-f.md) | Obtains **TagInfo** from **Want**, which is initialized by the NFC service and contains the attributes required by **TagInfo**. |
| [registerForegroundDispatch](arkts-connectivity-tag-registerforegrounddispatch-f.md) | Registers a listener for the NFC tag read event so that the tag can be preferentially dispatched to a foreground application. You can set the supported NFC tag technologies in **discTech**. The [TagInfo](arkts-connectivity-tag-taginfo-i.md) read is returned through a callback. This API can be called only by an application running in the foreground. It must be used with [tag.unregisterForegroundDispatch](arkts-connectivity-tag-unregisterforegrounddispatch-f.md) in pairs. The registered callback must be unregistered before the tag reading page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result. |
| [unregisterForegroundDispatch](arkts-connectivity-tag-unregisterforegrounddispatch-f.md) | Unregisters the listener for the NFC tag read event. If the listener is unregistered, the NFC tag discovered will not be dispatched to foreground applications. The registered callback must be unregistered before the tag reading page exits the foreground or is destroyed. |
| [on](arkts-connectivity-tag-on-f.md#onreadermode) | Subscribes to the NFC tag read event to implement dispatch of the tag to a foreground application preferentially. The device enters the reader mode and disables card emulation. You can set the supported NFC tag technologies in **discTech**. The [TagInfo](arkts-connectivity-tag-taginfo-i.md) read is returned through a callback. This API must be used with [tag.off](arkts-connectivity-tag-off-f.md#offreadermode) in pairs. If the NFC reader mode is enabled by **tag.on**, [tag.off](arkts-connectivity-tag-off-f.md#offreadermode) must be called when the application page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result. This API and tag.on are mutually exclusive. |
| [off](arkts-connectivity-tag-off-f.md#offreadermode) | Unsubscribes from the NFC tag card read event. The device exits the reader mode and resumes card emulation. If the NFC reader mode is enabled by tag.on, this API must be used when the application page exits the foreground or is destroyed. |
| [on](arkts-connectivity-tag-on-f.md#onreadermodewithinterval) | Subscribes to the NFC tag read event so that the tag can be preferentially dispatched to a foreground application. You can also set the interval for detecting whether a card is present. This API uses an asynchronous callback to return the result. |
| [off](arkts-connectivity-tag-off-f.md#offreadermodewithinterval) | Unsubscribes from the NFC tag card read event. The device exits the reader mode and resumes card emulation. If the NFC reader mode is enabled by tag.on, this API must be used when the application page exits the foreground or is destroyed. This API uses an asynchronous callback to return the result. |
| [getBarcodeTag](arkts-connectivity-tag-getbarcodetag-f.md) | Obtains a **BarcodeTag** object, which allows access to the tags in the BarcodeTag format. |

### Interfaces

| Name | Description |
| --- | --- |
| [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Before a card with tags is read or written, **[TagInfo](arkts-connectivity-tag-taginfo-i.md)** must be obtained to determine the tag technologies supported by the card. In this way, the application can invoke the correct API to communicate with the card. |
| [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md) | Defines an NDEF record. For details, see *NFCForum-TS-NDEF_1.0*. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [TagInfo](arkts-connectivity-tag-taginfo-i-sys.md) | Before a card with tags is read or written, **[TagInfo](arkts-connectivity-tag-taginfo-i.md)** must be obtained to determine the tag technologies supported by the card. In this way, the application can invoke the correct API to communicate with the card. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [NfcATag](arkts-connectivity-tag-nfcatag-t.md) | Obtains an **NfcATag** object. |
| [NfcBTag](arkts-connectivity-tag-nfcbtag-t.md) | Obtains an **NfcBTag** object. |
| [NfcFTag](arkts-connectivity-tag-nfcftag-t.md) | Obtains an **NfcFTag** object. |
| [NfcVTag](arkts-connectivity-tag-nfcvtag-t.md) | Obtains an **NfcVTag** object. |
| [IsoDepTag](arkts-connectivity-tag-isodeptag-t.md) | Obtains an **IsoDepTag** object. |
| [NdefTag](arkts-connectivity-tag-ndeftag-t.md) | Obtains an **NdefTag** object. |
| [MifareClassicTag](arkts-connectivity-tag-mifareclassictag-t.md) | Obtains a **MifareClassicTag** object. |
| [MifareUltralightTag](arkts-connectivity-tag-mifareultralighttag-t.md) | Obtains a **MifareUltralightTag** object. |
| [NdefFormatableTag](arkts-connectivity-tag-ndefformatabletag-t.md) | Obtains a **NdefFormatableTag** object. |
| [NdefMessage](arkts-connectivity-tag-ndefmessage-t.md) | Obtains an **NdefMessage** object. |
| [TagSession](arkts-connectivity-tag-tagsession-t.md) | Obtains a **TagSession** object. |
| [BarcodeTag](arkts-connectivity-tag-barcodetag-t.md) | Obtains a **BarcodeTag** object. |

### Enums

| Name | Description |
| --- | --- |
| [TnfType](arkts-connectivity-tag-tnftype-e.md) | Enumerates the TNF types. For details, see *NFCForum-TS-NDEF_1.0*. |
| [NfcForumType](arkts-connectivity-tag-nfcforumtype-e.md) | Enumerates the NFC Forum tag types. |
| [MifareClassicType](arkts-connectivity-tag-mifareclassictype-e.md) | Enumerates the MIFARE Classic tag types. |
| [MifareClassicSize](arkts-connectivity-tag-mifareclassicsize-e.md) | Enumerates the sizes of a MIFARE Classic tag. |
| [MifareUltralightType](arkts-connectivity-tag-mifareultralighttype-e.md) | Enumerates the MIFARE Ultralight tag types. |

### Constants

| Name | Description |
| --- | --- |
| [NFC_A](arkts-connectivity-tag-con.md#nfc_a) | NFC-A (ISO 14443-3A). |
| [NFC_B](arkts-connectivity-tag-con.md#nfc_b) | NFC-B (ISO 14443-3B). |
| [ISO_DEP](arkts-connectivity-tag-con.md#iso_dep) | ISO-DEP (ISO 14443-4). |
| [NFC_F](arkts-connectivity-tag-con.md#nfc_f) | NFC-F (JIS 6319-4). |
| [NFC_V](arkts-connectivity-tag-con.md#nfc_v) | NFC-V (ISO 15693). |
| [NDEF](arkts-connectivity-tag-con.md#ndef) | NDEF. |
| [NDEF_FORMATABLE](arkts-connectivity-tag-con.md#ndef_formatable) | NDEF formattable. |
| [MIFARE_CLASSIC](arkts-connectivity-tag-con.md#mifare_classic) | MIFARE Classic. |
| [MIFARE_ULTRALIGHT](arkts-connectivity-tag-con.md#mifare_ultralight) | MIFARE Ultralight. |
| [RTD_TEXT](arkts-connectivity-tag-con.md#rtd_text) | NDEF record of the text type. For details, see **NFCForum-TS-NDEF_1.0**. |
| [RTD_URI](arkts-connectivity-tag-con.md#rtd_uri) | NDEF record of the URI type. For details, see **NFCForum-TS-NDEF_1.0**. |
| [NFC_BARCODE](arkts-connectivity-tag-con.md#nfc_barcode) | BARCODE technology. |
| [SKIP_NDEF](arkts-connectivity-tag-con.md#skip_ndef) | Method used to skip the NDEF check. |
