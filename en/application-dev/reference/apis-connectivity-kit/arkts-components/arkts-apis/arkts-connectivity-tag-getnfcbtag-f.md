# getNfcBTag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcBTag

```TypeScript
function getNfcBTag(tagInfo: TagInfo): NfcBTag
```

Obtains an **NfcBTag** object, which allows access to the tags that use the NFC-B technology.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [tag.getNfcB](arkts-connectivity-tag-getnfcb-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getNfcB](arkts-connectivity-tag-getnfcb-f.md)

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [NfcBTag](arkts-connectivity-tag-nfcbtag-t.md) | **NfcBTag** object obtained. |
