# getNfcVTag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcVTag

```TypeScript
function getNfcVTag(tagInfo: TagInfo): NfcVTag
```

Obtains an **NfcVTag** object, which allows access to the tags that use the NFC-V technology.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [tag.getNfcV](arkts-connectivity-tag-getnfcv-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getNfcV](arkts-connectivity-tag-getnfcv-f.md)

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [NfcVTag](arkts-connectivity-tag-nfcvtag-t.md) | **NfcVTag** object obtained. |
