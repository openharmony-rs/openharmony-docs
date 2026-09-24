# @ohos.fontManager(Font Management)

This module provides the application with the capabilities to install, uninstall, query third-party fonts, and monitor the status of font services. Specifically, it includes: <br>- Installing application-level or session-level font files, supporting formats such as `.ttf`, `.ttc`, and `.otf`. <br>- Uninstalling installed fonts based on the font path. <br>- Querying the scope of application for installed fonts. <br>- Registering a font service status listener to notify the application when the font service abnormally exits.

**Since:** 26.0.1

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
| [installScopeFont](arkts-localization-fontmanager-installscopefont-f.md) | Install the font file in the specified path as an application-level or session-level font. This API uses a promise to return the result. |
| [offFontObserver](arkts-localization-fontmanager-offfontobserver-f.md) | Unregisters the font service status listener. |
| [onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md) | Registers a listener for monitoring the font service status. |
| [uninstallScopeFont](arkts-localization-fontmanager-uninstallscopefont-f.md) | Uninstall installed application-level or session-level fonts based on the font path. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [dataMigration](arkts-localization-fontmanager-datamigration-f-sys.md) | Data migration API used during device upgrades to start a migration task, providing real-time feedback on migration progress and results through a callback function. |
| [installFont](arkts-localization-fontmanager-installfont-f-sys.md) | Installs a font file from a specified path into the system font library. This API uses a promise to return the result. |
| [uninstallFont](arkts-localization-fontmanager-uninstallfont-f-sys.md) | Uninstalls an installed font file from the system font library by font name. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | Font service status listener. |

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
| [FontScope](arkts-localization-fontmanager-fontscope-e.md) | An enumeration representing the scope of font application. |
