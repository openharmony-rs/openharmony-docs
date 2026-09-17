# MediaChangeRequest

Media change request, which is the parent class of the asset change request and album change request.

> **NOTE:** 
> 
> The media change request takes effect only after
> [applyChanges](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#applychanges) is called.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## comment

```TypeScript
readonly comment: string
```

A readonly member for type checking.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
