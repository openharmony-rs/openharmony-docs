# ChangeData

Defines the return value of the listener callback.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraUris

```TypeScript
extraUris: Array<string>
```

URIs of the changed files in the album. The value may be undefined. Check whether the value is undefined before using it.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## type

```TypeScript
type: NotifyType
```

Notification type.

**Type:** [NotifyType](arkts-medialibrary-photoaccesshelper-notifytype-e.md)

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## uris

```TypeScript
uris: Array<string>
```

All URIs with the same [NotifyType](arkts-medialibrary-photoaccesshelper-notifytype-e.md), which can be **PhotoAsset** or **Album**.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
