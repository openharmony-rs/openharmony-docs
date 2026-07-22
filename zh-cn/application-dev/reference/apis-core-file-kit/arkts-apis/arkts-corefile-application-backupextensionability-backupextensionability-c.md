# BackupExtensionAbility

备份恢复扩展能力。应用可通过该类实现自定义备份、恢复、进度上报和安全退出逻辑。

**起始版本：** 10

<!--Device-unnamed-declare class BackupExtensionAbility--><!--Device-unnamed-declare class BackupExtensionAbility-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

## 导入模块

```TypeScript
import { BundleVersion } from '@kit.CoreFileKit';
```

## onBackup

```TypeScript
onBackup(): void
```

Extension生命周期回调，在执行备份数据时回调，由开发者实现自定义备份数据处理。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onBackup(): void--><!--Device-BackupExtensionAbility-onBackup(): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**示例：**

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

备份恢复框架在备份时向应用传递扩展参数，由开发者实现自定义备份处理。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onBackupEx(backupInfo: string): string | Promise<string>--><!--Device-BackupExtensionAbility-onBackupEx(backupInfo: string): string | Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backupInfo | string | 是 | 备份时框架传递给应用的扩展信息，参数为JSON格式字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用执行自定义备份操作的信息，返回值为JSON格式字符串，包含type、errorCode和errorInfo字段，支持同步返回或使用Promise异步返回。 |

**示例：**

```TypeScript
import { BackupExtensionAbility } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  onBackupEx(backupInfo: string): string {
    try {
      if (backupInfo == '') {
        // 当backupInfo为空时，应用根据业务自行做处理。
        console.info('backupInfo is empty');
      }
      console.info(`onBackupEx ok`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: 0,
        errorInfo: 'app customized error info'
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`BackupExt error. Code:${error.code}, message:${error.message}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: error.code,
        errorInfo: error.message
      }
      return JSON.stringify(errorInfo);
    }
  }
} 

```

```TypeScript
import { BackupExtensionAbility } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  // 异步实现
  async onBackupEx(backupInfo: string): Promise<string> {
    try {
      if (backupInfo == '') {
        // 当backupInfo为空时，应用根据业务自行做处理。
        console.info('backupInfo is empty');
      }
      console.info(`onBackupEx ok`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: 0,
        errorInfo: 'app customized error info'
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`BackupExt error. Code:${error.code}, message:${error.message}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: error.code,
        errorInfo: error.message
      }
      return JSON.stringify(errorInfo);
    }
  }
} 

```

## onProcess

```TypeScript
onProcess(): string
```

返回应用执行备份或恢复业务的进度信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onProcess(): string--><!--Device-BackupExtensionAbility-onProcess(): string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用处理数据的进度信息，返回值为JSON格式字符串。 |

**示例：**

```TypeScript
import { BackupExtensionAbility } from '@kit.CoreFileKit';
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Sendable
class MigrateProgressInfo {
  private migrateProgress: string = '';
  private name: string = 'test'; // appName
  private processed: number = 0; // 已处理的数据
  private total: number = 100; // 总数
  private isPercentage: boolean = true // 可选字段，true表示需要按百分比的格式化展示进度，false或者不实现该字段表示按具体项数展示进度

  getMigrateProgress(): string {
    this.migrateProgress = `{"progressInfo": [{"name": "${this.name}", "processed": "${this.processed}", "total": "${
      this.total}", "isPercentage": "${this.isPercentage}"}]}`;
    return this.migrateProgress;
  }

  updateProcessed(processed: number) {
    this.processed = processed;
  }
}

class BackupExt extends BackupExtensionAbility {
  private progressInfo: MigrateProgressInfo = new MigrateProgressInfo();

  // 如下代码中，appJob方法为模拟的实际业务代码，args为appJob方法的参数，用于提交到taskpool中，开启子线程进行工作
  async onBackup() {
    console.info(`onBackup begin`);
    let args = 100; // args为appJob方法的参数
    let jobTask: taskpool.Task = new taskpool.LongTask(appJob, this.progressInfo, args);
    try {
      await taskpool.execute(jobTask, taskpool.Priority.LOW);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`onBackup error. Code: ${err.code}, message: ${err.message}`);
    }
    taskpool.terminateTask(jobTask); // 需要手动销毁
    console.info(`onBackup end`);
  }

  async onRestore() {
    console.info(`onRestore begin`);
    let args = 100; // args为appJob方法的参数
    let jobTask: taskpool.Task = new taskpool.LongTask(appJob, this.progressInfo, args);
    try {
      await taskpool.execute(jobTask, taskpool.Priority.LOW);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`onRestore error. Code: ${err.code}, message: ${err.message}`);
    }
    taskpool.terminateTask(jobTask); // 需要手动销毁
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
  // 在业务执行时刷新已处理进度
  let currentProcessed: number = 0;
  // 模拟业务实际逻辑
  for (let i = 0; i < args; i++) {
    currentProcessed = i;
    progressInfo.updateProcessed(currentProcessed);
  }
  return 'ok';
}

```

## onRelease

```TypeScript
onRelease(scenario: number): Promise<void>
```

备份恢复框架安全退出回调，应用可在备份或恢复完成后清理临时文件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onRelease(scenario: int): Promise<void>--><!--Device-BackupExtensionAbility-onRelease(scenario: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scenario | number | 是 | 当前操作场景，值为1表示备份，值为2表示恢复。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例：**

```TypeScript
// 以清理文件为例
import { BackupExtensionAbility, fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

const SCENARIO_BACKUP: number = 1;
const SCENARIO_RESTORE: number = 2;
// 需要清理的临时目录
let filePath: string = '/data/storage/el2/base/.temp/';

class BackupExt extends BackupExtensionAbility {
  async onRelease(scenario: number): Promise<void> {
    try {
      if (scenario == SCENARIO_BACKUP) {
        // 备份场景，应用自行实现处理，以清理备份产生的临时文件为例
        console.info(`onRelease begin`);
        await fileIo.rmdir(filePath);
        console.info(`onRelease end, rmdir succeed`);
      }
      if (scenario == SCENARIO_RESTORE) {
        // 恢复场景，应用自行实现处理，以清理恢复产生的临时文件为例
        console.info(`onRelease begin`);
        await fileIo.rmdir(filePath);
        console.info(`onRelease end, rmdir succeed`);
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`onRelease failed with error. Code: ${err.code}, message: ${err.message}`);
    }
  }
}

```

## onRestore

```TypeScript
onRestore(bundleVersion: BundleVersion): void
```

Extension生命周期回调，在执行恢复数据时回调，由开发者提供扩展的恢复数据操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onRestore(bundleVersion: BundleVersion): void--><!--Device-BackupExtensionAbility-onRestore(bundleVersion: BundleVersion): void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleVersion | [BundleVersion](arkts-corefile-application-backupextensionability-bundleversion-i.md) | 是 | 恢复时应用数据所在的版本信息。 |

**示例：**

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

Extension生命周期回调，在执行恢复数据时回调，由开发者实现自定义恢复数据处理。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string | Promise<string>--><!--Device-BackupExtensionAbility-onRestoreEx(bundleVersion: BundleVersion, restoreInfo: string): string | Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleVersion | [BundleVersion](arkts-corefile-application-backupextensionability-bundleversion-i.md) | 是 | 恢复时应用数据所在的版本信息。 |
| restoreInfo | string | 是 | 恢复时框架传递给应用的扩展信息，参数为JSON格式字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用执行自定义恢复操作的信息，返回值为JSON格式字符串，包含type、errorCode和errorInfo字段，支持同步返回或使用Promise异步返回。 |

**示例：**

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}
class BackupExt extends BackupExtensionAbility {
  // 异步实现
  async onRestoreEx(bundleVersion : BundleVersion, restoreInfo: string): Promise<string> {
    try {
      if (restoreInfo == '') {
        // 当restoreInfo为空时，应用根据业务自行做处理。
        console.info('restoreInfo is empty');
      }
      console.info(`onRestoreEx ok ${JSON.stringify(bundleVersion)}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: 0,
        errorInfo: 'app customized error info'
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`onRestoreEx error. Code:${error.code}, message:${error.message}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: error.code,
        errorInfo: error.message
      }
      return JSON.stringify(errorInfo);
    }
  }
}

```

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
interface ErrorInfo {
  type: string,
  errorCode: number,
  errorInfo: string
}

class BackupExt extends BackupExtensionAbility {
  // 同步实现
  onRestoreEx(bundleVersion : BundleVersion, restoreInfo: string): string {
    try {
      if (restoreInfo == '') {
        // 当restoreInfo为空时，应用根据业务自行做处理。
        console.info('restoreInfo is empty');
      }
      console.info(`onRestoreEx ok ${JSON.stringify(bundleVersion)}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: 0,
        errorInfo: 'app customized error info'
      }
      return JSON.stringify(errorInfo);
    } catch (err) {
      let error: BusinessError = err as BusinessError;
      console.error(`onRestoreEx error. Code:${error.code}, message:${error.message}`);
      let errorInfo: ErrorInfo = {
        type: 'ErrorInfo',
        errorCode: error.code,
        errorInfo: error.message
      }
      return JSON.stringify(errorInfo);
    }
  }
}


```

## context

```TypeScript
context: BackupExtensionContext
```

BackupExtensionAbility的上下文环境，继承自ExtensionContext。

**类型：** BackupExtensionContext

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackupExtensionAbility-context: BackupExtensionContext--><!--Device-BackupExtensionAbility-context: BackupExtensionContext-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

