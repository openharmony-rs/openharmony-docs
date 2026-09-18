# getNfcATag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcATag

```TypeScript
function getNfcATag(tagInfo: TagInfo): NfcATag
```

Obtains an **NfcATag** object, which allows access to the tags that use the NFC-A technology.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [tag.getNfcA](arkts-connectivity-tag-getnfca-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getNfcA](arkts-connectivity-tag-getnfca-f.md)

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [NfcATag](arkts-connectivity-tag-nfcatag-t.md) | **NfcATag** object obtained. |
