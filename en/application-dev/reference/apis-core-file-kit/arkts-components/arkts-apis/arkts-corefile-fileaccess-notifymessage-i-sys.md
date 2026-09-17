# NotifyMessage (System API)

Represents the notification message.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** WatchEvent

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## type

```TypeScript
type: NotifyType
```

Notification type.

**Type:** [NotifyType](arkts-corefile-cloudsync-notifytype-e.md)

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## uris

```TypeScript
uris: Array<string>
```

URIs of the changed files. Currently, only one notification is supported. A collection of multiple notifications will be supported in later versions.

**Type:** Array&lt;string&gt;

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
