# ndef(Standard NFC Tags)

```TypeScript
namespace ndef
```

Provides methods for accessing NDEF tag.

**Since:** 9

<!--Device-tag-namespace ndef--><!--Device-tag-namespace ndef-End-->

**System capability:** SystemCapability.Communication.NFC.Tag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createNdefMessage](arkts-connectivity-ndef-createndefmessage-f.md#createndefmessage) | Creates an NDEF message from raw byte data. The data must comply with the NDEF record format. Otherwise, the NDEF record list contained in the **NdefMessage** object will be empty. |
| [createNdefMessage](arkts-connectivity-ndef-createndefmessage-f.md#createndefmessage) | Creates an NDEF message from the NDEF records list. |
| [makeApplicationRecord](arkts-connectivity-ndef-makeapplicationrecord-f.md#makeapplicationrecord) | Creates an NDEF record based on the specified application bundle name. |
| [makeExternalRecord](arkts-connectivity-ndef-makeexternalrecord-f.md#makeexternalrecord) | Creates an NDEF record based on application-specific data. |
| [makeMimeRecord](arkts-connectivity-ndef-makemimerecord-f.md#makemimerecord) | Creates an NDEF record based on the specified MIME data and type. |
| [makeTextRecord](arkts-connectivity-ndef-maketextrecord-f.md#maketextrecord) | Creates an NDEF record based on the specified text data and language type. |
| [makeUriRecord](arkts-connectivity-ndef-makeurirecord-f.md#makeurirecord) | Creates an NDEF record based on the specified URI. |
| [messageToBytes](arkts-connectivity-ndef-messagetobytes-f.md#messagetobytes) | Converts an NDEF message to bytes. |
