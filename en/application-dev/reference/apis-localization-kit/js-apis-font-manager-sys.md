# @ohos.fontManager (Font Management) (System API)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=cc8fe8b0f1b2859346994908b98ebf9b3df1ff9d translatedAt=2026-07-17T00:24:29.342Z pushedAt=2026-07-17T10:11:25.291Z -->

This module provides system applications with the capabilities to install and uninstall third-party fonts and migrate font data. Specifically:

- Installing font files from a specified path (.ttf and .ttc formats are supported).

- Uninstalling installed fonts by font name.

- Starting a font data migration task during device upgrades, and providing callbacks for migration progress and results.

>  **NOTE**
>  
>  - The initial APIs of this module are supported since API version 19. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  - The APIs provided by this module are system APIs.

## Modules to Import

```js
import { fontManager } from '@kit.LocalizationKit';
```

## installFont

installFont(path: string): Promise&lt;number&gt;

Installs a font file from a specified path into the system font library. This API uses a promise to return the result.

After successful installation, applications can use the font by its font name.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| path | string | Yes | Path to the font file to be installed. Only .ttf and .ttc font files are supported. |

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the installation result.<br>- The value **0** indicates that the installation is successful and the font has been added to the system font library.<br>- Any other value indicates that the installation failed. Troubleshoot based on the error code. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31100101 | The font does not exist.      |
| 31100102 | The font is not supported.    |
| 31100103 | Failed to copy the font file. |
| 31100104 | The font file is installed.   |
| 31100105 | Exceeded the maximum number of installed files. |
| 31100106 | The system capability works abnormally. |

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function installFont() {
    try {
      let res = await fontManager.installFont('fontPath');
      console.info('installFont suc. res is ' + res);
    } catch (error) {
      console.error('installFont err.' + error.code);
    }
    return;
  }
  ```

## uninstallFont

uninstallFont(fullName: string): Promise&lt;number&gt;

Uninstalls an installed font file from the system font library by font name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| fullName | string | Yes    | Name of the font to be uninstalled. You can open the .ttf or .ttc font file to obtain the name.<br>The font name is case-sensitive. Ensure that it exactly matches the actual font name. |

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the uninstallation result.<br>- The value **0** indicates that the uninstallation is successful and the font has been removed from the system font library.<br>- Any other value indicates that the uninstallation failed. Troubleshoot based on the error code. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31100107 | The font file does not exist. |
| 31100108 | Failed to delete the font file. |
| 31100109 | The system ability works abnormally. |

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function uninstallFont() {
    try {
      let res = await fontManager.uninstallFont('fontName');
      console.info('uninstallFont suc. res is ' + res);
    } catch (error) {
      console.error('uninstallFont err.' + error.code);
    }
    return;
  }
  ```

## dataMigration<sup>23+</sup>

dataMigration(callback: DataMigrationCallback): number

Data migration API used during device upgrades to start a migration task, providing real-time feedback on migration progress and results through a callback function.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| callback | [DataMigrationCallback](#datamigrationcallback23) | Yes   | Callback function for data migration.|

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| number | Result of the migration task startup.<br>- **0**: The migration task is started successfully. The migration task will be executed in the background and the progress and result will be notified through the callback.<br>- Other values: The migration task failed to start. Troubleshoot based on the error code. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 31100110 | Call failed due to system error. |
| 31100111 | Data migration is in progress. |

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress: (progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult: (result : number) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
  }
  ```

## DataMigrationCallback<sup>23+</sup>

Callback API type used during data migration, defining the callback methods for the data migration process. You must implement all methods of this API to receive heartbeat notifications, progress updates, and the final result during migration.

### onHeartBeat<sup>23+</sup>

onHeartBeat(): void

Callback function that is periodically invoked during the execution of the data migration task to notify you that the migration task is still running normally. You can use it to update UI prompts or execute other business logic.

**System capability**: SystemCapability.Global.FontManager

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress: (progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult: (result : number) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
  }
  ```

### onProgress<sup>23+</sup>

onProgress(progress : DataMigrationProgress): void

Callback function that is periodically invoked during the execution of the data migration task to notify you of the current migration progress and estimated remaining time. This callback can be used when progress bars, remaining time, and other information need to be displayed on the UI.

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| progress | [DataMigrationProgress](#datamigrationprogress23) | Yes  | Data migration progress.|

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress: (progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult: (result : number) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
  }
  ```

### onResult<sup>23+</sup>

onResult(result : number): void

Callback function that is invoked after the data migration task is completed (whether successful or failed) to notify you of the final migration result. This callback can be used when subsequent operations (such as updating the UI, logging, notifying users, etc.) need to be performed after migration is complete.

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| result | number | Yes | Data migration result.<br>**0**: Data migration succeeded.<br>**1**: No data migration is required.<br>**2**: Failed to obtain the user ID.<br>**3**: Failed to check the directory.<br>**4**: Failed to initialize the cache directory.<br>**5**: Failed to open the source file.<br>**6**: Copy failed.<br>**7**: File rename failed.<br>**8**: File deletion failed.|

**Example:**

  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async function dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress: (progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult: (result : number) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
  }
  ```

## DataMigrationProgress<sup>23+</sup>

Describes the progress information of data migration, including the progress percentage and estimated remaining time. This API is the parameter type of the `onProgress` API in the data migration callback.

**System capability**: SystemCapability.Global.FontManager

| Name    | Type| Read-Only| Optional   | Description |
| -------- | ---------------|--------|---------|-------------------------------- |
| timeRemaining | number  | Yes | No | Estimated remaining time, which may vary depending on factors such as device performance, file size, and system load.<br>The value must be a non-negative integer, with a minimum value of 0.<br>The unit is seconds.    |
| progressPercentage | number | Yes | No | Data migration progress percentage, which is calculated based on the number or size of migrated font files and may not increase evenly. When `progressPercentage` reaches `100`, the migration task is about to complete and the `onResult` callback is about to be invoked.<br>The value range is [0, 100].|