# @ohos.fontManager(Font Management)

This module provides system applications with the capabilities to install and uninstall third-party fonts and migrate font data. Specifically: <br>- Installing font files from a specified path (.ttf and .ttc formats are supported). <br>- Uninstalling installed fonts by font name. <br>- Starting a font data migration task during device upgrades, and providing callbacks for migration progress and results.

**Since:** 26.1.0

**System capability:** SystemCapability.Global.FontManager

## Modules to Import

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getFontScope](arkts-localization-fontmanager-getfontscope-f.md) | Queries the scope of a font by URL. This API uses a promise to return the result. |
| [installScopeFont](arkts-localization-fontmanager-installscopefont-f.md) | Installs a scope font file from a specified path into the system font library. This API uses a promise to return the result. |
| [offFontObserver](arkts-localization-fontmanager-offfontobserver-f.md) | Unregisters the font service death observer. |
| [onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md) | Registers a font service death observer. When the font service dies unexpectedly, the [onServiceDied](arkts-localization-fontmanager-fontclientobserver-i.md#onservicedied) callback is invoked. |
| [uninstallScopeFont](arkts-localization-fontmanager-uninstallscopefont-f.md) | Uninstalls a scope font file from the system font library by URL. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md) | Data migration API used during device upgrades to start a migration task, providing real-time feedback on migration progress and results through a callback function. |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md) | Installs a font file from a specified path into the system font library. This API uses a promise to return the result. After successful installation, applications can use the font by its font name. |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md) | Uninstalls an installed font file from the system font library by font name. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | Observer for font service death events. When the font service dies unexpectedly, the [onServiceDied](arkts-localization-fontmanager-fontclientobserver-i.md#onservicedied) callback is invoked. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | Callback API type used during data migration, defining the callback methods for the data migration process. You must implement all methods of this API to receive heartbeat notifications, progress updates, and the final result during migration. |
| [DataMigrationProgress](arkts-localization-fontmanager-datamigrationprogress-i-sys.md) | Describes the progress information of data migration, including the progress percentage and estimated remaining time. This API is the parameter type of the `onProgress` API in the data migration callback. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [FontScope](arkts-localization-fontmanager-fontscope-e.md) | Enumerates the font scopes. |
