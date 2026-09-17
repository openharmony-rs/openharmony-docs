# @ohos.update

The **@ohos.update** module provides the core capabilities of online update, local SD card update, and factory reset. Version management, update control, and equipment maintenance can be implemented for the Over-The-Air (OTA) clients and system apps using this module. APIs provided by this module can be used for system version update, offline update, and data clearing.

This module implements update of the entire system, including built-in resources and preset applications, but not third-party apps. This feature ensures system integrity, prevents compatibility issues with third-party apps, and improves update stability and security.

There are two types of updates: local SD card update and OTA update.

The design logic and use scenarios of each update type are as follows:

- **Local SD card update:** For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

Use scenarios: The system needs to be updated from a local storage device.

**Benefits**

This update mode applies to system update offline or with poor network connection when automatic update cannot be implemented. This mode does not depend on the upgrade package management server, reducing the update cost.

- **Online update:** For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md.)

Use scenarios: The system needs to be automatically checked and updated by connecting to the network.

This update mode is implemented by calling APIs of the **Updater** module. This mode depends on the upgrade package management server deployed by the vendor (the server system provides functions such as version check and upgrade package download). The APIs are implemented by the vendor.

**Benefits**

Users can obtain system updates in a timely manner, improving update efficiency and user experience. Functions such as automatic version check, background download, and resumable download are supported, reducing operation costs for users.

**Reset**

Use scenarios: This operation is performed to delete user data and restore the device to factory settings. It is applicable to scenarios such as troubleshooting, device transfer or scrapping, privacy protection, and storage space release. Traditional reset methods have problems such as residual data, uncleared keys, and incomplete data cleanup. This module provides hierarchical restoration capabilities to meet different security requirements.

**Benefits**

This module enables users to quickly troubleshoot, free up storage space, and protect the security of privacy data. Three reset modes are provided to meet the requirements for different security levels. Common reset applies to routine maintenance scenarios, forcible reset applies to data destruction scenarios, and deep reset applies to extreme scenarios such as device scrapping. In this way, hierarchical management of data clearing is implemented, reducing O&M costs.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs. For details about the system application permission request, see the system application development guide. For details about the application extension permission request, see the application extension development guide.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getLocalUpdater](arkts-basicservices-update-getlocalupdater-f-sys.md) | Obtains a **LocalUpdater** object, which is used to upgrade the system from a local storage device (such as the SD card). After this API is called, the system returns the **LocalUpdater** utility object, which provides functions such as verifying and installing the local upgrade package. |
| [getOnlineUpdater](arkts-basicservices-update-getonlineupdater-f-sys.md) | Obtains an **OnlineUpdater** object, which can be used to check for new versions online, download update packages, and install update packages. This API can be used in scenarios such as OTA upgrade (for details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)) of client applications and online system upgrade. This API can help users obtain system updates in a timely manner, improving upgrade efficiency and user experience. |
| [getRestorer](arkts-basicservices-update-getrestorer-f-sys.md) | Obtains a **Restorer** object for restoring factory settings. After this API is called, the system returns the **Restorer** utility object. Three factory reset methods are provided: |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BusinessType](arkts-basicservices-update-businesstype-i-sys.md) | Represents an upgrade service type. |
| [CheckResult](arkts-basicservices-update-checkresult-i-sys.md) | Indicates the version check result. |
| [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | Defines the clearing options, which specify the errors to be cleared. |
| [ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md) | Represents a component description file. |
| [CurrentVersionInfo](arkts-basicservices-update-currentversioninfo-i-sys.md) | Represents information about the current version. |
| [DescriptionInfo](arkts-basicservices-update-descriptioninfo-i-sys.md) | Represents information about the version description file. |
| [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | Defines the description options, which specifies the format and language of the description file. The object contains the **format** and **language** fields. **format** indicates the description file format, which can be **STANDARD** or **SIMPLIFIED**. **language** indicates the language code, which can be **zh-cn**. |
| [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | Defines the download options, including the **allowNetwork** and **order** fields, which are used to control the download behavior. |
| [ErrorMessage](arkts-basicservices-update-errormessage-i-sys.md) | Represents an error message. |
| [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | Represents event type information. |
| [EventInfo](arkts-basicservices-update-eventinfo-i-sys.md) | Defines an **EventInfo** object, which is used to receive the event details transferred by upgrade event notification. The object contains the **eventId** and **taskBody** fields. **eventId** indicates the event ID, which identifies the event type; **taskBody** indicates the task data, which contains the task status and progress. |
| [FactoryResetInfo](arkts-basicservices-update-factoryresetinfo-i-sys.md) | Describes the information of restoring factory settings. |
| [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | Represents the factory reset strategy, which contains the **scope** (reset scope) and **strategy** (reset strategy description) fields. |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | Defines a tool class for updating the local firmware, such as verifying the signature and integrity of the local upgrade package, installing the local upgrade package, and listening for local upgrade events. |
| [NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md) | Represents information about the new version. |
| [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | Defines the pausing download options, which are used to control the pause behavior. The object contains the **isAllowAutoResume** field. The value **true** indicates that automatically resuming download is allowed, and the value **false** indicates that download needs to be manually resumed. |
| [Restorer](arkts-basicservices-update-restorer-i-sys.md) | Defines a tool class for restoring factory settings, such as clearing data in the user partition, deeply clearing data in the user and OS partitions, and synchronously clearing file keys. |
| [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | Defines the resuming download options, which are used to specify the network type for resuming download. The object includes the **allowNetwork** field, which specifies the network type allowed for download. |
| [TaskBody](arkts-basicservices-update-taskbody-i-sys.md) | Represents task data. |
| [TaskInfo](arkts-basicservices-update-taskinfo-i-sys.md) | Represents the task information. |
| [Updater](arkts-basicservices-update-updater-i-sys.md) | Defines a utility class that provides online system update functions, such as checking new versions online, downloading upgrade packages, installing update packages, managing upgrade policies, and obtaining version information. |
| [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | Represents the upgrade file, including the file type and file path, which are used to specify the local upgrade package to be installed. |
| [UpgradeInfo](arkts-basicservices-update-upgradeinfo-i-sys.md) | Represents update information. |
| [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | Defines the upgrade options, which are used to specify the upgrade operation type. |
| [UpgradePeriod](arkts-basicservices-update-upgradeperiod-i-sys.md) | Represents an automatic upgrade period. |
| [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | Sets the upgrade policy to control the upgrade behavior. |
| [VersionComponent](arkts-basicservices-update-versioncomponent-i-sys.md) | Represents a version component. |
| [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Represents version digest information. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [BusinessSubType](arkts-basicservices-update-businesssubtype-e-sys.md) | Represents an update type. |
| [BusinessVendor](arkts-basicservices-update-businessvendor-e-sys.md) | Represents a device vendor. |
| [ComponentType](arkts-basicservices-update-componenttype-e-sys.md) | Represents a component type. |
| [DescriptionFormat](arkts-basicservices-update-descriptionformat-e-sys.md) | Enumerates description file formats. |
| [DescriptionType](arkts-basicservices-update-descriptiontype-e-sys.md) | Enumerates description file types. |
| [EffectiveMode](arkts-basicservices-update-effectivemode-e-sys.md) | Enumerates effective modes. |
| [EventClassify](arkts-basicservices-update-eventclassify-e-sys.md) | Represents an event type. |
| [EventId](arkts-basicservices-update-eventid-e-sys.md) | Enumerates event IDs. |
| [FactoryResetScope](arkts-basicservices-update-factoryresetscope-e-sys.md) | Describes the scope of restoring factory settings. |
| [NetType](arkts-basicservices-update-nettype-e-sys.md) | Enumerates the network types allowed for download. The value **CELLULAR** indicates that only download over the cellular network is allowed; **WiFi** that only download using Wi-Fi is allowed; **CELLULAR_AND_WIFI** indicates that download over both the cellular network and Wi-Fi is allowed. |
| [Order](arkts-basicservices-update-order-e-sys.md) | Enumerates update commands. |
| [OtaMode](arkts-basicservices-update-otamode-e-sys.md) | Enumerates the update modes. |
| [UpgradeAction](arkts-basicservices-update-upgradeaction-e-sys.md) | Represents an update mode. |
| [UpgradeStatus](arkts-basicservices-update-upgradestatus-e-sys.md) | Enumerates update states. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | Represents an event callback. |
<!--DelEnd-->
