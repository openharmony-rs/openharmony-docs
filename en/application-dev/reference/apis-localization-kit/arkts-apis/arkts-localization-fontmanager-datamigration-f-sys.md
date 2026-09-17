# dataMigration (System API)

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## dataMigration

```TypeScript
function dataMigration(callback: DataMigrationCallback): number
```

Data migration API used during device upgrades to start a migration task, providing real-time feedback on migration progress and results through a callback function.

**Since:** 23

**Required permissions:** ohos.permission.UPDATE_FONT

**System capability:** SystemCapability.Global.FontManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | Yes | Callback function for data migration. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result of the migration task startup.<br>- **0**: The migration task is started successfully. The migration task will be executed in the background and the progress and result will be notified through the callback. <br>- Other values: The migration task failed to start. Troubleshoot based on the error code. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [31100110](../errorcode-font-manager.md#31100110-failed-to-call-the-api-due-to-system-errors) | Call failed due to system error. |
| [31100111](../errorcode-font-manager.md#31100111-migration-task-being-executed) | Data migration is in progress. |
