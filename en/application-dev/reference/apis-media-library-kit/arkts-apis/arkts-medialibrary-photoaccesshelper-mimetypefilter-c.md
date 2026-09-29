# MimeTypeFilter

```TypeScript
class MimeTypeFilter
```

Describes the configuration for file type filtering.

**Since:** 19

<!--Device-photoAccessHelper-class MimeTypeFilter--><!--Device-photoAccessHelper-class MimeTypeFilter-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## mimeTypeArray

```TypeScript
mimeTypeArray: Array<string>
```

Types of media files that PhotoPicker allows users to filter by. The maximum array length is 10, thus supporting up to 10 specified types.

The filter type is defined by the MIME type, for example, image/jpeg and video/mp4.

**Type:** Array&lt;string&gt;

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-MimeTypeFilter-mimeTypeArray: Array<string>--><!--Device-MimeTypeFilter-mimeTypeArray: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
