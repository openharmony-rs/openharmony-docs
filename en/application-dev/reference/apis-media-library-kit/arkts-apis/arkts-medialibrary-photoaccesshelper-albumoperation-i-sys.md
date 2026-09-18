# AlbumOperation (System API)

Represents an album operation configuration.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## attr

```TypeScript
attr: AlbumAttribute
```

The album operation attribute.

**Type:** [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## type

```TypeScript
type: AlbumOperationType
```

The album operation type.

**Type:** [AlbumOperationType](arkts-medialibrary-photoaccesshelper-albumoperationtype-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## values

```TypeScript
values: string[]
```

The album operation parameters. The array can contain a maximum of 20 strings, and each string must not exceed 8KB.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
