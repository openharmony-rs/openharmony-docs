# @ohos.file.BackupExtensionContext (Backup and Restore Extension Capability)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b2b40ad27b0a04a8c75aa3540e06525fdca8ac20 translatedAt=2026-11-04T03:59:46.734Z pushedAt=2026-11-04T10:12:33.448Z nl=1 -->

BackupExtensionContext is the context of BackupExtensionAbility. It inherits from ExtensionContext and is used to obtain the temporary directory during backup and restore.

The BackupExtensionContext module provides the capability to access the resources of a specific BackupExtensionAbility. When an application implements the backup and restore extension capability, it can use this context to obtain the temporary directory corresponding to el1 (device-level encryption zone) or el2 (user-level encryption zone), which is used to temporarily save the data to be backed up or read the data to be restored. This simplifies the development of the backup and restore extension capability and isolates temporary data by data security level. For an extended BackupExtensionAbility, you can directly use BackupExtensionContext as the context, or define a type that inherits from BackupExtensionContext as the context.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { BackupExtensionContext } from '@kit.CoreFileKit';
```

## BackupExtensionContext

### Properties

**System capability**: SystemCapability.FileManagement.StorageService.Backup

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- |-------| -------- | -------- |
| backupDir | string | Yes| No| Temporary directory used for backup or restore. This directory cannot be used for other purposes. Currently, only the **el1** and **el2** directories are supported. If other directories are used, null is returned.|

### When to Use

**BackupExtensionContext** is used to obtain a temporary directory for backup or restore.

**Example**

```ts
import { BackupExtensionAbility } from '@kit.CoreFileKit';
import { contextConstant } from '@kit.AbilityKit';

export default class MyBackupExtAbility extends BackupExtensionAbility {
    async onBackup() {
        console.info('onBackup begin');
        // Set the encryption area to el1 (device-level encryption area).
        this.context.area = contextConstant.AreaMode.EL1;
        // Obtain the sandbox path through this.context.backupDir.
        let dir = this.context.backupDir;
        console.info(`onBackup el1 dir: ${dir}`);
        this.context.area = contextConstant.AreaMode.EL2;
        dir = this.context.backupDir;
        console.info(`onBackup el2 dir: ${dir}`);
        console.info('onBackup end');
    }

    async onRestore() {
        console.info('onRestore begin');
        // Set the encryption area to el1 (device-level encryption area).
        this.context.area = contextConstant.AreaMode.EL1;
        // Obtain the sandbox path through this.context.backupDir.
        let dir = this.context.backupDir;
        console.info(`onRestore el1 dir: ${dir}`);
        this.context.area = contextConstant.AreaMode.EL2;
        dir = this.context.backupDir;
        console.info(`onRestore el2 dir: ${dir}`);
        console.info('onRestore end');
    }
}
```
