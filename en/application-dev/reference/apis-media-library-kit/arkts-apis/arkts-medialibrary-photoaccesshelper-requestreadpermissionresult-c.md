# RequestReadPermissionResult

Request read permission result

**Since:** 23

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## authorizedUris

```TypeScript
authorizedUris?: Array<string>
```

URIs that have been created and granted the save permission.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## invalidUris

```TypeScript
invalidUris?: Array<string>
```

URIs that may be deleted, hidden, or renamed.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
