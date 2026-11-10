# @ohos.application.BackupExtensionAbility (Backup and Restore Extension Capability) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b2b40ad27b0a04a8c75aa3540e06525fdca8ac20 translatedAt=2026-11-10T05:07:15.880Z pushedAt=2026-11-10T07:31:50.586Z nl=1 -->

The **BackupExtensionAbility** module provides the system extension capability for backup and restore services. During the backup and restore phases, an application can return custom backup information and compatibility information to the caller, which is used to support the backup and restore framework in querying application capabilities, determining compatibility, and performing subsequent processing, thereby reducing the integration cost of capability negotiation and version compatibility determination before backup and restore.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs of this module. For details about other public APIs, see [@ohos.application.BackupExtensionAbility (Backup and Restore Extension Capability)](js-apis-application-backupExtensionAbility.md).
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { BackupExtensionAbility } from '@kit.CoreFileKit';
```

### getBackupInfo<sup>12+</sup>

getBackupInfo(): string

Executed when the caller queries application data, and the application returns custom backup information. This API is applicable to scenarios where the application needs to provide the caller with application data description, backup scope, or other custom information before backup.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Returns**

| Type                  | Description   |
| --------------------- | :---- |
| string | Application-defined backup information. The specific format and fields are defined by the application, and the caller parses them as agreed.|

**Example**

  ```ts
  class BackupExt extends BackupExtensionAbility {
    getBackupInfo(): string {
      console.info('getBackupInfo ok');
      let info = 'app diy info';
      return info;
    }
  }
  ```

### getBackupCompatibilityInfo<sup>20+</sup>

getBackupCompatibilityInfo(extInfo: string): Promise&lt;string&gt;

Executed during the application backup phase when the caller obtains the application's custom compatibility information, and implemented and returned by the application. A Promise is used for asynchronous callback.

This API is applicable to scenarios where the caller needs to be provided with compatibility information such as the database version, service capability switch, or whether backup is supported before backup. The specific format and fields of the compatibility information are defined by the application, and the caller parses them as agreed.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name       | Type                           | Mandatory| Description                          |
| ------------- | ------------------------------- | ---- | ------------------------------ |
| extInfo | string | Yes  | Extra information passed to the application. The implementation is determined by the application.|
**Returns**

| Type                  | Description   |
| --------------------- | :---- |
| Promise&lt;string&gt; | Promise used to return the application-defined compatibility information during the backup process.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  class BackupExt extends BackupExtensionAbility {
    async getBackupCompatibilityInfo(extInfo: string): Promise<string> {
      let ret: string = '';
      try {
        // Here JSON is used only as an example. The corresponding judgment logic and relevant fields should be customized by the application.
        if (!extInfo) {
          ret = '{"dbVersion": "1.0", "isThemCardEnable": "true"}';
        } else {
          let extJson: Record<string, string> = JSON.parse(extInfo);
          if (extJson?.requireCompatibility) {
            ret = '{"isSupportBackup": "true"}';
          } else {
            ret = '{"isSupportBackup": "false"}';
          }
        }
      } catch (error) {
        let err: BusinessError = error as BusinessError;
        console.error(`getBackupCompatibilityInfo failed with error. Code: ${err.code}, message: ${err.message}`);
      }
      return ret;
    }
  }
  ```

### getRestoreCompatibilityInfo<sup>20+</sup>

getRestoreCompatibilityInfo(extInfo: string): Promise&lt;string&gt;

Executed during the application restore phase when the caller obtains the application's custom compatibility information, and implemented and returned by the application. This API is applicable to scenarios where the caller needs to be provided with compatibility information such as the database version, service capability switch, or whether restore is supported before restore. The specific format and fields of the compatibility information are defined by the application, and the caller parses them as agreed. A Promise is used for asynchronous callback.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Backup

**Parameters**

| Name       | Type                           | Mandatory| Description                          |
| ------------- | ------------------------------- | ---- | ------------------------------ |
| extInfo | string | Yes  | Extra information passed to the application. The implementation is determined by the application.|
**Returns**

| Type                  | Description   |
| --------------------- | :---- |
| Promise&lt;string&gt; | Promise used to return the compatibility information customized by the application during the restore process.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  class BackupExt extends BackupExtensionAbility {
    async getRestoreCompatibilityInfo(extInfo: string): Promise<string> {
      let ret: string = '';
      try {
        // Here JSON is used only as an example. The corresponding judgment logic and relevant fields should be customized by the application.
        if (!extInfo) {
          ret = '{"dbVersion": "1.0", "isThemCardEnable": "true"}';
        } else {
          let extJson: Record<string, string> = JSON.parse(extInfo);
          if (extJson?.requireCompatibility) {
            ret = '{"isSupportRestore": "true"}';
          } else {
            ret = '{"isSupportRestore": "false"}';
          }
        }
      } catch (error) {
        let err: BusinessError = error as BusinessError;
        console.error(`getRestoreCompatibilityInfo failed with error. Code: ${err.code}, message: ${err.message}`);
      }
      return ret;
    }
  }
  ```
