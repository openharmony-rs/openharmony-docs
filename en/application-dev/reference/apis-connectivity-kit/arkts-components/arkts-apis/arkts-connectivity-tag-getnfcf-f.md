# getNfcF

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcF

```TypeScript
function getNfcF(tagInfo: TagInfo): NfcFTag
```

Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [NfcFTag](arkts-connectivity-tag-nfcftag-t.md) | **NfcFTag** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-tag-readwrite-error) | The tag running state is abnormal in the service. |
