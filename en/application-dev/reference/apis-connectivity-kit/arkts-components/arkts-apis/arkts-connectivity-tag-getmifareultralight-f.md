# getMifareUltralight

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getMifareUltralight

```TypeScript
function getMifareUltralight(tagInfo: TagInfo): MifareUltralightTag
```

Obtains a **MifareUltralightTag** object, which allows access to the tags that use MIFARE Ultralight.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Indicates the dispatched tag information. |

**Return value:**

| Type | Description |
| --- | --- |
| [MifareUltralightTag](arkts-connectivity-tag-mifareultralighttag-t.md) | **MifareUltralightTag** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
