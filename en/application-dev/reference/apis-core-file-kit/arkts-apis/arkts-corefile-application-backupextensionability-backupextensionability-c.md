# BackupExtensionAbility

Class to be override for backup extension ability.

**Since:** 10

**System capability:** SystemCapability.FileManagement.StorageService.Backup

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

```TypeScript
> NOTE
> 
> The following shows the sample code for asynchronous implementation.
```

## onProcess

```TypeScript
onProcess(): string
```

Callback to be called when getting backup/restore process info. Developer could override this method to provide the backup/restore process info.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

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

```TypeScript
> NOTE
> 
> The following shows the sample code for synchronous implementation.
```

## context

```TypeScript
context: BackupExtensionContext
```

Indicates backup extension ability context.

**Type:** [BackupExtensionContext](arkts-corefile-file-backupextensioncontext-backupextensioncontext-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup
