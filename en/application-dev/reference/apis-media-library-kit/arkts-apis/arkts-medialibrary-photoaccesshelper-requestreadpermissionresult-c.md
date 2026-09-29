# RequestReadPermissionResult

```TypeScript
export class RequestReadPermissionResult
```

Describes the authorized URIs and invalid URIs.

**Since:** 23

<!--Device-photoAccessHelper-export class RequestReadPermissionResult--><!--Device-photoAccessHelper-export class RequestReadPermissionResult-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-RequestReadPermissionResult-authorizedUris?: Array<string>--><!--Device-RequestReadPermissionResult-authorizedUris?: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## invalidUris

```TypeScript
invalidUris?: Array<string>
```

URIs that may be deleted, hidden, or renamed.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-RequestReadPermissionResult-invalidUris?: Array<string>--><!--Device-RequestReadPermissionResult-invalidUris?: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
