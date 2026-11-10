# AssetUriResult (System API)

```TypeScript
interface AssetUriResult
```

Describes the operation result of a media asset URI.

**Since:** 26.1.0

<!--Device-photoAccessHelper-interface AssetUriResult--><!--Device-photoAccessHelper-interface AssetUriResult-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## isSuccess

```TypeScript
readonly isSuccess: boolean
```

Whether the operation is successful. **true** if the operation is successful, **false** otherwise. If the operation fails, **resultUri** is an empty string.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssetUriResult-readonly isSuccess: boolean--><!--Device-AssetUriResult-readonly isSuccess: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## originalUri

```TypeScript
readonly originalUri: string
```

URI of the original asset corresponding to the operation.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssetUriResult-readonly originalUri: string--><!--Device-AssetUriResult-readonly originalUri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## resultUri

```TypeScript
readonly resultUri: string
```

URI of the asset corresponding to the operation result. The value is an empty string if the operation fails.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AssetUriResult-readonly resultUri: string--><!--Device-AssetUriResult-readonly resultUri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
