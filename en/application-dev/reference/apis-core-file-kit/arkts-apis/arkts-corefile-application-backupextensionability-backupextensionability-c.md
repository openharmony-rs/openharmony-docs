# BackupExtensionAbility

```TypeScript
declare class BackupExtensionAbility
```

Class to be override for backup extension ability.

**Since:** 10

<!--Device-unnamed-declare class BackupExtensionAbility--><!--Device-unnamed-declare class BackupExtensionAbility-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

## ExtensionAbility Usage Restrictions

To ensure system security and stability, BackupExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
```

## onBackup

```TypeScript
onBackup(): void
```

Callback to be called when the backup procedure is started. Developer could override this method to build files to be backup.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onBackup(): void--><!--Device-BackupExtensionAbility-onBackup(): void-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Examples**

```TypeScript
class BackupExt extends BackupExtensionAbility {
  async onBackup() {
    console.info('onBackup');
  }
}
```

## onBackupEx

```TypeScript
onBackupEx(backupInfo: string): string | Promise<string>
```

Callback to be called when the backup procedure is started. Developer could override this method to restore.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onBackupEx(backupInfo: string): string | Promise<string>--><!--Device-BackupExtensionAbility-onBackupEx(backupInfo: string): string | Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backupInfo | string | Yes | BackupInfo to be backup, the param is a JSON string, it is an array, each array element includes detail and type now. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; Promise&lt;string&gt; | Return backup result, support promise, the result is a JSON string, it includes type, errorCode and errorInfo now. |

**Examples**

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';

interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  onBackupEx(backupInfo: string): string {
    try {
      if (backupInfo == "") {
        // If backupInfo is empty, the application processes the data based on the service.
        console.info("backupInfo is empty");
      }
      console.info(`onBackupEx ok`);
      let errorInfo: ErrorInfo = {
        type: "ErrorInfo",
        errorCode: 0,
        errorInfo: "app customized error info"
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      console.error(`BackupExt error. Code:${err.code}, message:${err.message}`);
    }
    return "";
  }
}
```

> NOTE
> 
> The following shows the sample code for asynchronous implementation.

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';

interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  // Asynchronous implementation
  async onBackupEx(backupInfo: string): Promise<string> {
    try {
      if (backupInfo == "") {
        // If backupInfo is empty, the application processes the data based on the service.
        console.info("backupInfo is empty");
      }
      console.info(`onBackupEx ok`);
      let errorInfo: ErrorInfo = {
        type: "ErrorInfo",
        errorCode: 0,
        errorInfo: "app customized error info"
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      console.error(`BackupExt error. Code:${err.code}, message:${err.message}`);
    }
    return "";
  }
}
```

## onProcess

```TypeScript
onProcess(): string
```

Callback to be called when getting backup/restore process info. Developer could override this method to provide the backup/restore process info.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onProcess(): string--><!--Device-BackupExtensionAbility-onProcess(): string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the backup/restore process info. |

**Examples**

```TypeScript
import { BackupExtensionAbility } from '@kit.CoreFileKit';
import { taskpool } from '@kit.ArkTS';

@Sendable
class MigrateProgressInfo {
  private migrateProgress: string = '';
  private name: string = "test"; // appName
  private processed: number = 0; // Processed data
  private total: number = 100; // Total number
  private isPercentage: boolean = true // (Optional) The value true means to display the progress in percentage; the value false or an unimplemented field means to display the progress by the number of items.

  getMigrateProgress(): string {
    this.migrateProgress = `{"progressInfo": [{"name": ${this.name}, "processed": ${this.processed}, "total": ${
      this.total}, "isPercentage": ${this.isPercentage}}]}`;
    return this.migrateProgress;
  }

  updateProcessed(processed: number) {
    this.processed = processed;
  }
}

class BackupExt extends BackupExtensionAbility {
  private progressInfo: MigrateProgressInfo = new MigrateProgressInfo();

  // In the following code, the appJob method is the simulated service code, and args specifies the parameters of appJob(). This method is used to start a worker thread in the task pool.
  async onBackup() {
    console.info(`onBackup begin`);
    let args = 100; // args is a parameter of appJob().
    let jobTask: taskpool.Task = new taskpool.LongTask(appJob, this.progressInfo, args);
    try {
      await taskpool.execute(jobTask, taskpool.Priority.LOW);
    } catch (error) {
      console.error("onBackup error." + error.message);
    }
    taskpool.terminateTask(jobTask); // Manually destroy the task.
    console.info(`onBackup end`);
  }

  async onRestore() {
    console.info(`onRestore begin`);
    let args = 100; // args is a parameter of appJob().
    let jobTask: taskpool.Task = new taskpool.LongTask(appJob, this.progressInfo, args);
    try {
      await taskpool.execute(jobTask, taskpool.Priority.LOW);
    } catch (error) {
      console.error("onRestore error." + error.message);
    }
    taskpool.terminateTask(jobTask); // Manually destroy the task.
    console.info(`onRestore end`);
  }


  onProcess(): string {
    console.info(`onProcess begin`);
    return this.progressInfo.getMigrateProgress();
  }
}

@Concurrent
function appJob(progressInfo: MigrateProgressInfo, args: number) : string {
  console.info(`appJob begin, args is: ` + args);
  // Update the processing progress during service execution.
  let currentProcessed: number = 0;
  // Simulate the actual service logic.
  for (let i = 0; i < args; i++) {
    currentProcessed = i;
    progressInfo.updateProcessed(currentProcessed);
  }
  return "ok";
}
```

## onRelease

```TypeScript
onRelease(scenario: number): Promise<void>
```

Callback to be called before extension ability exits. Developer could override this method to clean abnormal data.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onRelease(scenario: int): Promise<void>--><!--Device-BackupExtensionAbility-onRelease(scenario: int): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scenario | number | Yes | The value 1 indicates backup and the value 2 indicates restoration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function |

**Examples**

```TypeScript
// The following describes an example of removing files.
import { BackupExtensionAbility, fileIo } from '@kit.CoreFileKit';

const SCENARIO_BACKUP: number = 1;
const SCENARIO_RESTORE: number = 2;
// Temporary directory to be removed.
let filePath: string = '/data/storage/el2/base/.temp/';

class BackupExt extends BackupExtensionAbility {
  async onRelease(scenario: number): Promise<void> {
    try {
      if (scenario == SCENARIO_BACKUP) {
        // In the backup scenario, the application implements the processing. The following describes how to remove temporary files generated during backup.
        console.info(`onRelease begin`);
        await fileIo.rmdir(filePath);
        console.info(`onRelease end, rmdir succeed`);
      }
      if (scenario == SCENARIO_RESTORE) {
        // In the restore scenario, the application implements the processing. The following describes how to remove temporary files generated during restoration.
        console.info(`onRelease begin`);
        await fileIo.rmdir(filePath);
        console.info(`onRelease end, rmdir succeed`);
      }
    } catch (error) {
      console.error(`onRelease failed with error. Code: ${error.code}, message: ${error.message}`);
    }
  }
}
```

## onRestore

```TypeScript
onRestore(bundleVersion: BundleVersion): void
```

Callback to be called when the restore procedure is started. Developer could override this method to restore from copies for various bundle versions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onRestore(bundleVersion: BundleVersion): void--><!--Device-BackupExtensionAbility-onRestore(bundleVersion: BundleVersion): void-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleVersion | [BundleVersion](arkts-corefile-application-backupextensionability-bundleversion-i.md) | Yes | Bundle version to be restore. |

**Examples**

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';

class BackupExt extends BackupExtensionAbility {
  async onRestore(bundleVersion : BundleVersion) {
    console.info(`onRestore ok ${JSON.stringify(bundleVersion)}`);
  }
}
```

## onRestoreEx

```TypeScript
onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string | Promise<string>
```

Callback to be called when the restore procedure is started. Developer could override this method to restore.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string | Promise<string>--><!--Device-BackupExtensionAbility-onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string | Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleVersion | [BundleVersion](arkts-corefile-application-backupextensionability-bundleversion-i.md) | Yes | Bundle version to be restore. |
| restoreInfo | string | Yes | RestoreInfo to be restore, the param is a JSON string, it is an array, each array element includes detail and type now. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; Promise&lt;string&gt; | Return restore result, support promise. the result is a JSON string, it includes type, errorCode and errorInfo now. |

**Examples**

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  // Asynchronous implementation
  async onRestoreEx(bundleVersion : BundleVersion, restoreInfo: string): Promise<string> {
    try {
      if (restoreInfo == "") {
        // If restoreInfo is empty, the application processes the data based on the service.
        console.info("restoreInfo is empty");
      }
      console.info(`onRestoreEx ok ${JSON.stringify(bundleVersion)}`);
      let errorInfo: ErrorInfo = {
        type: "ErrorInfo",
        errorCode: 0,
        errorInfo: "app customized error info"
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      console.error(`onRestoreEx error. Code:${err.code}, message:${err.message}`);
    }
    return "";
  }
}
```

> NOTE
> 
> The following shows the sample code for synchronous implementation.

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}

class BackupExt extends BackupExtensionAbility {
  // Synchronous implementation
  onRestoreEx(bundleVersion : BundleVersion, restoreInfo: string): string {
    try {
      if (restoreInfo == "") {
        // If restoreInfo is empty, the application processes the data based on the service.
        console.info("restoreInfo is empty");
      }
      console.info(`onRestoreEx ok ${JSON.stringify(bundleVersion)}`);
      let errorInfo: ErrorInfo = {
        type: "ErrorInfo",
        errorCode: 0,
        errorInfo: "app customized error info"
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      console.error(`onRestoreEx error. Code:${err.code}, message:${err.message}`);
    }
    return "";
  }
}
```

## context

```TypeScript
context: BackupExtensionContext
```

Indicates backup extension ability context.

**Type:** [BackupExtensionContext](arkts-corefile-file-backupextensioncontext-backupextensioncontext-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-context: BackupExtensionContext--><!--Device-BackupExtensionAbility-context: BackupExtensionContext-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

## Appendix

BackupExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ability Kit | [@ohos.abilityAccessCtrl](../../apis-ability-kit/arkts-apis/arkts-ability-abilityaccessctrl.md) |
| Ability Kit | [@ohos.app.ability.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-missionmanager.md) |
| Ability Kit | [@ohos.app.ability.quickFixManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-quickfixmanager.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Ability Kit | [@ohos.application.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-application-missionmanager.md) |
| Ability Kit | [@ohos.bundle.appControl](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-appcontrol.md) |
| Ability Kit | [@ohos.bundle.bundleMonitor](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-bundlemonitor.md) |
| Ability Kit | [@ohos.bundle.defaultAppManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-defaultappmanager.md) |
| Ability Kit | [@ohos.bundle.distributedBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-distributedbundlemanager.md) |
| Ability Kit | [@ohos.bundle.freeInstall](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-freeinstall.md) |
| Ability Kit | [@ohos.bundle.innerBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-innerbundlemanager.md) |
| Ability Kit | [@ohos.bundle.installer](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-installer.md) |
| Ability Kit | [@ohos.bundle.launcherBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-launcherbundlemanager.md) |
| Background Tasks Kit | [@ohos.bundleState](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-bundlestate.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| Mdm Kit | [enterprise.dataTimeManager](../../apis-mdm-kit/arkts-apis/arkts-enterprise-datatimemanager.md) |
| Core File Kit | [@ohos.file.fileAccess](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileaccess.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Input Kit | [@ohos.multimodalInput.inputMonitor](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-inputmonitor.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.usageStatistics](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-usagestatistics.md) |
| ArkUI | [@ohos.screen](../../apis-arkui/arkts-apis/arkts-arkui-screen.md) |
| Sensor Service Kit | [@ohos.sensor](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-sensor.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [@ohos.update](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-update.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
