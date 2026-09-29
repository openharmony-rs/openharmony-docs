# TextContextInfo

```TypeScript
interface TextContextInfo
```

Represents the text information about the recommended images.

**Since:** 12

<!--Device-photoAccessHelper-interface TextContextInfo--><!--Device-photoAccessHelper-interface TextContextInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## text

```TypeScript
text?: string
```

Text based on which images are recommended. The text cannot exceed 250 characters. The default value is an empty string.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-TextContextInfo-text?: string--><!--Device-TextContextInfo-text?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
