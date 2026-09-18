# PhotoSelectResult

Defines information about the images or videos selected.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [PhotoSelectResult](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoselectresult-c.md)

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## isOriginalPhoto

```TypeScript
isOriginalPhoto: boolean
```

Whether the selected image is the original one. The value **true** means the selected image is the original one; the value **false** means the opposite.

**Type:** boolean

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [isOriginalPhoto](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoselectresult-c.md#isoriginalphoto)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.UserFileService

## photoUris

```TypeScript
photoUris: Array<string>
```

URIs of the media files selected. This URI array can be used only by [photoAccessHelper.getAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets). For details, see [Using a Media File URI](../../../file-management/user-file-uri-intro.md#using-a-media-file-uri).

**Type:** Array&lt;string&gt;

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [photoUris](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoselectresult-c.md#photouris)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.UserFileService
