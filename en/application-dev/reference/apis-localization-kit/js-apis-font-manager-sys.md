# @ohos.fontManager (Font Management) (System API)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=a04b9be3bedef1b09b05f9b1b2ad2d7c971b4692 translatedAt=2026-11-04T04:13:53.225Z pushedAt=2026-11-04T10:13:14.921Z nl=1 -->

This module provides system applications with the capabilities of installing and uninstalling third-party fonts and migrating font data. Specifically:
- Installs a font file from a specified path. The `.ttf`, `.ttc`, and `.otf` formats are supported.
- Uninstalls an installed font by its name.
- Starts a font data migration task during device upgrade, and provides callbacks for the migration progress and result.

>  **NOTE**
>  
>  - The initial APIs of this module are supported since API version 19. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  - This topic describes only the system APIs provided by this module. For details about its public APIs, see [@ohos.fontManager (Font Management)](js-apis-font-manager.md).

## Modules to Import

```js
import { fontManager } from '@kit.LocalizationKit';
```

## fontManager.installFont

installFont(path: string): Promise&lt;number&gt;

Installs the font file at the specified path into the system font library. This API uses a promise to return the result asynchronously.
> **NOTE**
>
> - After the installation is successful, the application can use the font by its font name. The same font path cannot be installed repeatedly.
>
> - The maximum number of font files that can be installed is 200. Since version 26.0.1, the maximum number of font files that can be installed on PC/2in1 and Tablet is 800.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters** 

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| path | string | Yes | Path of the font file to be installed. Only font files in `.ttf`, `.ttc`, and `.otf` formats are supported. |

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the installation result.<br>- Returns 0: the installation is successful, and the font has been added to the system font library.<br>- Returns other values: the installation fails. Check the error code to identify the cause. |

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
| 31100106 | The system ability works abnormally. |

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

## fontManager.uninstallFont

uninstallFont(fullName: string): Promise&lt;number&gt;

Uninstalls the installed font file from the system font library by font name. This API uses a promise to return the result asynchronously.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters** 

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| fullName | string | Yes | Name of the font to be uninstalled, which can be obtained by opening the `.ttf`, `.ttc`, and `.otf` font files.<br>The font name is case-sensitive. Ensure that it is exactly the same as the actual font name. |

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the uninstall result.<br>- Returns 0 if the uninstall is successful and the font has been removed from the system font library.<br>- Returns another value if the uninstall fails. Check the error code to identify the cause.|

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

## fontManager.dataMigration<sup>23+</sup>

dataMigration(callback: DataMigrationCallback): number

Data migration interface used during device upgrade. It starts a migration task and provides real-time feedback on the migration progress and result through a callback function.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters** 

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| callback | [DataMigrationCallback](#datamigrationcallback23) | Yes   | Callback function for data migration.|

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| number | Result of starting the migration task.<br>- 0: The migration task is started successfully and will be executed in the background, with the progress and result notified through the callback.<br>- Other values: The migration task fails to start. Troubleshoot the cause based on the error code. |

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

Callback interface type used during data migration. It defines the callback methods in the data migration process. Developers must implement all methods of this interface to receive heartbeat notifications, progress updates, and the final result during migration.

### onHeartBeat<sup>23+</sup>

onHeartBeat(): void

Callback function invoked periodically during the execution of a data migration task to notify developers that the migration task is still running normally. Developers can update the UI prompt or execute other business logic accordingly.

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

Callback function invoked periodically during the execution of a data migration task to notify developers of the current migration progress and estimated remaining time. Use this callback when the progress bar, remaining time, and other information need to be displayed on the UI.

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

Callback function invoked after a data migration task is completed (regardless of success or failure) to notify developers of the final migration result. Use this callback when subsequent operations need to be performed after migration is completed, such as updating the UI, recording logs, and notifying users.

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| result | number | Yes | Data migration result.<br>**0**: Data migration succeeded.<br>**1**: No data migration required.<br>**2**: Failed to obtain the user ID.<br>**3**: Failed to check the directory.<br>**4**: Failed to initialize the cache directory.<br>**5**: Failed to open the source file.<br>**6**: Copy failed.<br>**7**: File rename failed.<br>**8**: File deletion failed. |

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

Describes the progress information of data migration, including the progress percentage and estimated remaining time. This interface is the parameter type of the onProgress method of the data migration callback.

**System capability**: SystemCapability.Global.FontManager

| Name    | Type| Read-Only| Optional   | Description |
| -------- | ---------------|--------|---------|-------------------------------- |
| timeRemaining | number  |Yes | No | Estimated remaining time, which may vary depending on factors such as device performance, file size, and system load.<br>The value is a non-negative integer, with a minimum value of 0.<br>The unit is s.    |
| progressPercentage | number |Yes | No | Percentage progress of data migration. The progress value is calculated based on the number or size of migrated font files and may not increase evenly. When progressPercentage is 100, the migration task is about to complete and the onResult callback is about to be invoked.<br>The value ranges from 0 to 100.|