# getOnlineUpdater (System API)

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getOnlineUpdater

```TypeScript
function getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater
```

Obtains an **OnlineUpdater** object, which can be used to check for new versions online, download update packages, and install update packages. This API can be used in scenarios such as OTA upgrade (for details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)) of client applications and online system upgrade. This API can help users obtain system updates in a timely manner, improving upgrade efficiency and user experience.

**Overview**

This API obtains an **OnlineUpdater** object through the system service interface. The object provides core functions such as checking for new versions, downloading update packages, and installing update packages.

**Constraints**

- The upgrade package management server deployed by the vendor is required for checking for new versions and  
downloading update packages.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| upgradeInfo | [UpgradeInfo](arkts-basicservices-update-upgradeinfo-i-sys.md) | Yes | **UpgradeInfo** is the upgrade object information, which is used to identify the caller and upgrade service type. **upgradeApp** is the package name of the caller. The value is a string of 1 to 255 characters in the format **com.***xxx.xxx.xxx*. The length of each segment ranges from 1 to 64 characters. Only letters, digits, and periods (.) are supported. Each segment must start with a letter and cannot contain consecutive periods (.) or start or end with a period (.). If the value is out of range or the format is incorrect, an exception is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| [Updater](arkts-basicservices-update-updater-i-sys.md) | Utility object used to perform online update operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Define an UpgradeInfo object.
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // App package name
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // Vendor type
      subType: update.BusinessSubType.FIRMWARE // The update type is firmware.
    }
  };  
  // Obtain an OnlineUpdater object.
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
```
