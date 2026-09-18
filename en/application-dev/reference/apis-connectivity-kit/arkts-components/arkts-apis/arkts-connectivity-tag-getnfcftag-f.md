# getNfcFTag

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getNfcFTag

```TypeScript
function getNfcFTag(tagInfo: TagInfo): NfcFTag
```

Obtains an **NfcFTag** object, which allows access to the tags that use the NFC-F technology.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [tag.getNfcF](arkts-connectivity-tag-getnfcf-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getNfcF](arkts-connectivity-tag-getnfcf-f.md)

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tagInfo | [TagInfo](arkts-connectivity-tag-taginfo-i.md) | Yes | Tag information, including the tag technology type and related parameters, obtained from [tag.getTagInfo(want: Want)](arkts-connectivity-tag-gettaginfo-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [NfcFTag](arkts-connectivity-tag-nfcftag-t.md) | **NfcFTag** object obtained. |
