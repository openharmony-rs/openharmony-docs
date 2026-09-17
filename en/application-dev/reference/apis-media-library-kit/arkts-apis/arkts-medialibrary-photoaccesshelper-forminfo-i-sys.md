# FormInfo (System API)

Defines the Gallery widget information.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## formId

```TypeScript
formId: string
```

Widget ID, which is provided when a widget is created in Gallery.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

URI of the image bound to the widget. When a widget is created, **uri** can be empty or the URI of an image. When a widget is removed, **uri** is not verified and can be empty.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
