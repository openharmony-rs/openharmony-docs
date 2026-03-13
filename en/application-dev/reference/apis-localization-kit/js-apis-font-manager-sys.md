# @ohos.fontManager (Font Management) (System API)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **fontManager** module provides APIs for system applications to install and uninstall third-party fonts.

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

Installs a font in the specified path. This API uses a promise to return the result.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| path | string | Yes   | Path of the font file to be installed.|

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the result. The value **0** indicates that the installation is successful, and any other value indicates that the installation has failed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission denied.                 |
| 202 | Non-system application.            |
| 31100101 | Font does not exist.          |
| 31100102 | Font is not supported.        |
| 31100103 | Font file copy failed.        |
| 31100104 | Font file installed.          |
| 31100105 | Exceeded maximum number of installed files.     |
| 31100106 | Other error.     |

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async installFont() {
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

Uninstalls a font by name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| fullName | string | Yes   | Name of the font to be uninstalled. You can obtain the font name by opening the **.ttf** or **.ttc** font file.|

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| Promise&lt;number&gt; | Promise used to return the result. The value **0** indicates that the uninstallation is successful, and any other value indicates that the uninstallation has failed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission denied.                |
| 202 | Non-system application.           |
| 31100107 | Font file does not exist.    |
| 31100108 | Font file delete error.      |
| 31100109 | Other error.                 |

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  async uninstallFont() {
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

dataMigration(callback: DataMigrationCallback): int

Starts a migration task during device upgrade.

**Required permissions**: ohos.permission.UPDATE_FONT

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name  | Type    | Mandatory  | Description   |
| ----- | ------ | ---- | ----- |
| callback | [DataMigrationCallback](#datamigrationcallback23) | Yes   | Callback function for data migration.|

**Return value**

| Type                   | Description                    |
| --------------------- | ---------------------- |
| int | Result of starting the data migration task. The value **0** indicates that the process is started successfully. Otherwise, the process fails to be started.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Font Management Error Codes](errorcode-font-manager.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission denied.                |
| 202 | Non-system application.           |
| 31100110 | System error.  |
| 31100111 | DataMigrationing.      |

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult(result : int) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

## DataMigrationCallback<sup>23+</sup>

Callback type used during data migration.

### onHeartBeat<sup>23+</sup>

onHeartBeat(): void

Callback function used to return the heartbeat callback.

**System capability**: SystemCapability.Global.FontManager

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult(result : int) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

### onProgress<sup>23+</sup>

onProgress(progress : DataMigrationProgress): void

Callback used to return the data migration progress.

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| progress | [DataMigrationProgress](#datamigrationprogress23) | Yes  | Data migration progress.|

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult(result : int) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

### onResult<sup>23+</sup>

onResult(result : int): void

Callback used to return the data migration result.

**System capability**: SystemCapability.Global.FontManager

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | ---------------------------------- |
| result | int | Yes  | Data migration result.<br>**0**: Data migration is successful.<br>**1**: No data migration required.<br>**2**: Failed to obtain the user ID.<br>**3**: Failed to check the directory.<br>**4**: Failed to initialize the cache directory.<br>**5**: Failed to open the source file.<br>**6**: Failed to copy the file.<br>**7**: Failed to rename the file.<br>**8**: Failed to delete the file.|

**Example:**
  ```ts
  import { fontManager } from '@kit.LocalizationKit';

  dataMigration() {
    const callback: fontManager.DataMigrationCallback = {
      onHeartBeat: () => {
        console.info('onHeartBeat callback');
      },
      onProgress(progress : fontManager.DataMigrationProgress) => {
        console.info('onProgress callback');
      },
      onResult(result : int) => {
        console.info('onResult callback');
      }
    }
    try {
      let res = await fontManager.dataMigration(callback);
      console.info('dataMigration suc. res is ' + res);
    } catch (error) {
      console.error('dataMigration err.' + error.code);
    }
    return;
  }
  ```

## DataMigrationProgress<sup>23+</sup>

Describes the data migration progress.

**System capability**: SystemCapability.Global.FontManager

| Name    | Type| Read-Only| Optional   | Description |
| -------- | ---------------|--------|---------|-------------------------------- |
| timeRemaining | int  |Yes| No| Estimated remaining time, in seconds.   |
| progressPercentage | int |Yes| No| Data migration progress, in percentage. The value ranges from 0 to 100.|
