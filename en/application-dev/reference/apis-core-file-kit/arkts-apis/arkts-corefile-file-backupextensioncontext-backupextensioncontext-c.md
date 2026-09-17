# BackupExtensionContext

The context of an ability or an application. It allows access to application-specific resources. Can only be obtained through the ability.

@extends ExtensionContext

**Inheritance/Implementation:** BackupExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Backup

## Modules to Import

```TypeScript
import { BackupExtensionContext } from '@kit.CoreFileKit';
```

## backupDir

```TypeScript
readonly backupDir: string
```

Indicates backup dir.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup
