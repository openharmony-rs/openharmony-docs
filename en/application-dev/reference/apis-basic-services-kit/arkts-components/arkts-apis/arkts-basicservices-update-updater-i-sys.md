# Updater (System API)

Defines a utility class that provides online system update functions, such as checking new versions online, downloading upgrade packages, installing update packages, managing upgrade policies, and obtaining version information.

Use scenarios: OTA upgrade, online system upgrade, automatic version check, and upgrade management.

**Benefits**

Users can obtain system updates in a timely manner, improving upgrade efficiency and user experience and reducing operation costs. Functions such as automatic version check, background download, and resumable transfer are supported.

**Online upgrade**

**Implementation mechanism**

- Version check: Query requests about the new version information can be sent to the upgrade package management  
server.  
- Download management: Network type selection, pause/resume download, and resumable transfer are supported.  
- Installation mechanism: After the upgrade package is downloaded, it is unzipped and written to the system  
partition to prepare for restarting the app.  
- Status management: Maintain the upgrade task status, including querying task information, clearing abnormal  
status, and terminating the upgrade.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## checkNewVersion

```TypeScript
checkNewVersion(callback: AsyncCallback<CheckResult>): void
```

Checks whether a new version is available. The result includes whether a new version is available, new version number, and version digest information.

After the API is successfully called, the version check result is returned. The result can be used to determine whether an upgrade is required and provide version identifiers for subsequent operations such as download and upgrade. This API uses an asynchronous callback to return the result.

This API is the first one used in the online update process. The returned **versionDigestInfo** is mandatory for subsequent APIs.

After this API is called, you can call **getNewVersionInfo** to obtain detailed information about the new version, **download** to download the upgrade package, and **upgrade** to install the upgrade package.

**versionDigestInfo** returned by this API are mandatory for the subsequent APIs. These APIs can be called only when **isExistNewVersion** is **true**.

If the value of **isExistNewVersion** is **false**, the current version is the latest version. In this case, you do not need to perform the subsequent upgrade operations.

Use scenarios: Quickly check whether a new version is available and obtain the version digest information. Users can learn about the system update status in a timely manner, providing a basis for upgrade decisions.

**Overview**

This API sends a version check request to the upgrade package management server deployed by the vendor. The request carries parameters such as the current version information and device model. The server checks whether a new version is available based on the request parameters and returns the version check result (**CheckResult**), including the **isExistNewVersion** flag and **newVersionInfo** structure (version digest and version number).

The check process is as follows: The developer constructs request parameters. The system initiates an HTTP request. The server queries the version information. The system parses the response. The system returns the result.

**Constraints**

- This method depends on the upgrade package management server deployed by the vendor. Ensure that the server is  
properly deployed and accessible.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[CheckResult](arkts-basicservices-update-checkresult-i-sys.md)&gt; | Yes | Callback used to receive the version check result. The callback parameters include **err** and **checkResult**. **err** is **null** when the operation is successful; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Check for a new version and obtain the check result using a callback.
  onlineUpdater.checkNewVersion((checkNewVersionError: BusinessError,  
    checkResult: update.CheckResult) => {
      // Handle the error.
      if (checkNewVersionError) {
        console.error(`checkNewVersion error, code:${checkNewVersionError.code}, message:${checkNewVersionError.message}.`);
        return;
      }
      console.info(`checkNewVersion isExistNewVersion  ${checkResult?.isExistNewVersion}`);
    });
} catch (error) {
  let errInfo: BusinessError = error as BusinessError;
  console.error(`Failed to get updater. Code: ${errInfo.code}, message: ${errInfo.message}.`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
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
  // Check for a new version.
  onlineUpdater.checkNewVersion().then((result: update.CheckResult) => {
    console.info(`checkNewVersion isExistNewVersion: ${result.isExistNewVersion}`);
    // Version digest information
    console.info(`checkNewVersion versionDigestInfo: ${result.newVersionInfo.versionDigestInfo.versionDigest}`);
    }).catch((checkNewVersionError: BusinessError) => {
      console.error(`checkNewVersion promise error, code:${checkNewVersionError.code}, message:${checkNewVersionError.message}.`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to checkNewVersion. Code: ${err.code}, message: ${err.message}.`);
}
```

## checkNewVersion

```TypeScript
checkNewVersion(): Promise<CheckResult>
```

Checks whether a new version is available. The result includes whether a new version is available, new version number, and version digest information.

After the API is successfully called, the version check result is returned. The result can be used to determine whether an upgrade is required and provide version identifiers for subsequent operations such as download and upgrade. This API uses a promise to return the result.

This API is the first one used in the online update process. The returned **versionDigestInfo** is mandatory for subsequent APIs.

After this API is called, you can call **getNewVersionInfo** to obtain detailed information about the new version, **download** to download the upgrade package, and **upgrade** to install the upgrade package.

**versionDigestInfo** returned by this API are mandatory for the subsequent APIs. These APIs can be called only when **isExistNewVersion** is **true**.

If the value of **isExistNewVersion** is **false**, the current version is the latest version. In this case, you do not need to perform the subsequent upgrade operations.

Use scenarios: Quickly check whether a new version is available and obtain the version digest information. Users can learn about the system update status in a timely manner, providing a basis for upgrade decisions.

**Overview**

This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This API sends a version check request to the upgrade package management server deployed by the vendor. The request carries parameters such as the current version information and device model. The server checks whether a new version is available based on the request parameters and returns the version check result (**CheckResult**), including the **isExistNewVersion** flag and **newVersionInfo** structure (version digest and version number).

The check process is as follows: The developer constructs request parameters. The system initiates an HTTP request. The server queries the version information. The system parses the response. The system returns the result.

**Constraints**

- This method depends on the upgrade package management server deployed by the vendor. Ensure that the server is  
properly deployed and accessible.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CheckResult](arkts-basicservices-update-checkresult-i-sys.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is the version check result. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [checkNewVersion](#checknewversion)

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback<void>): void
```

Clears errors. When the upgrade package fails to be downloaded or installed, delete the downloaded files and clear errors. After the API is successfully called, errors are cleared and the upgrade is restored to the initial state. You can start the complete upgrade process from the step of **checkNewVersion**. This API uses an asynchronous callback to return the result.

Use scenarios: Clear errors and restart the upgrade after the upgrade fails.

**Overview**

The process is as follows: Verify the **clearOptions** parameter, and ensure that the value of **status** is **UPGRADE_FAIL**. Delete the local upgrade package file to release storage space. Clear errors in the system service. Reset the task status to the initial state. Clear the error information cache. After errors are cleared, the upgrade service is restored to the available state. You can call **checkNewVersion** to restart upgrade. Errors can be cleared only in the **UPGRADE_FAIL** state. If this API is called in other states, an error is returned.

**Constraints**

- If the **upgrade** method fails (the status is **UPGRADE_FAIL**), you must call **clearError** to clear the  
abnormal status.  
- If **clearError** is not called to clear errors, the upgrade process cannot be restarted.  
- After errors are cleared, you can restart the upgrade process from the step of **checkNewVersion**.

**Related methods**

- **upgrade()**: installs the upgrade package. If the operation fails, call **clearError**.  
- **checkNewVersion()**: checks for a new version again. This API should be called after errors are cleared.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| clearOptions | [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | Yes | Clearing options, which specify the errors to be cleared. The **status** field must be **UPGRADE_FAIL**. If the upgrade fails, the system retains the error state to prevent the upgrade from being performed again. In this case, you need to pass **UPGRADE_FAIL** so that errors can be cleared, and the system can be restored to the initial state to restart the upgrade process. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the result of clearing errors. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for clearing errors
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
try {
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
  // Clear errors and use a callback to return the result.
  onlineUpdater.clearError(versionDigestInfo, clearOptions, (clearFailError: BusinessError) => {
    if (clearFailError) {
      // Error clearing fails.
      console.error(`clearError execute error. code:${clearFailError.code}, message:${clearFailError.message}.`);
    } else {
      // Error clearing succeeds.
      console.info(`clearError execute success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for clearing errors
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
try {
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
  // Clear errors.
  onlineUpdater.clearError(versionDigestInfo, clearOptions).then(() => {
    console.info(`clearError execute success`);
  }).catch((clearFailError: BusinessError) => {
    console.error(`clearError execute error. code:${clearFailError.code}, message:${clearFailError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise<void>
```

Clears errors. When the upgrade package fails to be downloaded or installed, delete the downloaded files and clear errors. After the API is successfully called, errors are cleared and the upgrade is restored to the initial state. You can start the complete upgrade process from the step of **checkNewVersion**. This API uses a promise to return the result.

Use scenarios: Clear errors and restart the upgrade after the upgrade fails.

**Overview**

The process is as follows: Verify the **clearOptions** parameter, and ensure that the value of **status** is **UPGRADE_FAIL**. Delete the local upgrade package file to release storage space. Clear errors in the system service. Reset the task status to the initial state. Clear the error information cache. After errors are cleared, the upgrade service is restored to the available state. You can call **checkNewVersion** to restart upgrade. Errors can be cleared only in the **UPGRADE_FAIL** state. If this API is called in other states, an error is returned.

**Constraints**

- If the **upgrade** method fails (the status is **UPGRADE_FAIL**), you must call **clearError** to clear the  
abnormal status.  
- If **clearError** is not called to clear errors, the upgrade process cannot be restarted.  
- After errors are cleared, you can restart the upgrade process from the step of **checkNewVersion**.

**Related methods**

- **upgrade()**: installs the upgrade package. If the operation fails, call **clearError**.  
- **checkNewVersion()**: checks for a new version again. This API should be called after errors are cleared.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| clearOptions | [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | Yes | Clearing options, which specify the errors to be cleared. The **status** field must be **UPGRADE_FAIL**. If the upgrade fails, the system retains the error state to prevent the upgrade from being performed again. In this case, you need to pass **UPGRADE_FAIL** so that errors can be cleared, and the system can be restored to the initial state to restart the upgrade process. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [clearError](#clearerror)

## download

```TypeScript
download(
      versionDigestInfo: VersionDigestInfo,
      downloadOptions: DownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

Downloads the upgrade package to the device. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. Progress monitoring, pause, and resumption of download are supported, helping users efficiently obtain the upgrade package, saving bandwidth and time, and improving the upgrade success rate. This API uses an asynchronous callback to return the result.

Use scenarios: online update of the OTA client, automatic download of the upgrade package in the background, and resumable transfer after network interruption.

**Overview**

This method downloads the upgrade package from the upgrade package management server to the device. The download process is as follows:

Resumable transfer is supported. The number of bytes that have been downloaded and the network connection status are recorded. If the download is interrupted, it can resume from the breakpoint. When the download is paused, the progress status (such as the size of the data that has been downloaded and file path) is saved. When the download is resumed, the progress status is read to continue receiving data.

**Calling sequence**

- You must call **checkNewVersion** to check whether a new version is available and obtain the version digest  
information.  
- You must first call **checkNewVersion** to check whether a new version is available. This API can be called to  
download the upgrade package only when **isExistNewVersion** is **true**.  
- If the value of **isExistNewVersion** is **false**, no new version is available. If this method is called, a  
message will be returned, indicating that the current version is the latest version.

**Related methods**

- **checkNewVersion()**: checks whether a new version is available (prerequisite method).  
- **resumeDownload()**: resumes download (called after the download is paused).  
- **pauseDownload()**: pauses download (called during download).  
- **upgrade()**: installs the upgrade package (called after the download is complete).

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| downloadOptions | [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | Yes | Download options, which are used to control the download behavior. The **allowNetwork** field specifies the network type allowed for download. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package exceeds 100 MB, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the download result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Download options
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // Whether to allow download over data network
  order: update.Order.DOWNLOAD // Download
};
try {
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
  // Download the upgrade package.
  onlineUpdater.download(versionDigestInfo, downloadOptions, (downloadError: BusinessError) => {
    if (downloadError) {
      // Download failed.
      console.error(`download error. code:${downloadError.code}, message:${downloadError.message}.`);
    } else {
      // The download is successful.
      console.info(`download success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Download options
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // Whether to allow download over data network
  order: update.Order.DOWNLOAD // Download
};
try {
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
  // Download the upgrade package.
  onlineUpdater.download(versionDigestInfo, downloadOptions).then(() => {
    console.info(`download start`);
  }).catch((downloadError: BusinessError) => {
    console.error(`download error. code:${downloadError.code}, message:${downloadError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## download

```TypeScript
download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise<void>
```

Downloads the upgrade package to the device. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. Progress monitoring, pause, and resumption of download are supported,

helping users efficiently obtain the upgrade package, saving bandwidth and time, and improving the upgrade success rate. This API uses a promise to return the result.

Use scenarios: online update of the OTA client, automatic download of the upgrade package in the background, and resumable transfer after network interruption.

**Overview**

This method downloads the upgrade package from the upgrade package management server to the device. The download process is as follows:

Resumable transfer is supported. The number of bytes that have been downloaded and the network connection status are recorded. If the download is interrupted, it can resume from the breakpoint. When the download is paused, the progress status (such as the size of the data that has been downloaded and file path) is saved. When the download is resumed, the progress status is read to continue receiving data.

**Calling sequence**

- You must call **checkNewVersion** to check whether a new version is available and obtain the version digest  
information.  
- This method can be called to download the upgrade package only when the value of **isExistNewVersion** is  
**true** by calling **checkNewVersion**.  
- If the value of **isExistNewVersion** is **false**, no new version is available. If this method is called, a  
message will be returned, indicating that the current version is the latest version.

**Related methods**

- **checkNewVersion()**: checks whether a new version is available (prerequisite method).  
- **resumeDownload()**: resumes download (called after the download is paused).  
- **pauseDownload()**: pauses download (called during download).  
- **upgrade()**: installs the upgrade package (called after the download is complete).

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| downloadOptions | [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | Yes | Download options, which are used to control the download behavior. The **allowNetwork** field specifies the network type allowed for download. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package exceeds 100 MB, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value, indicating that the download task is started successfully. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [download](#download)

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

Obtains the description of the current version. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After this API is called successfully, the current version description array is returned, which can be used for version information display, version status confirmation, and version comparison and analysis. This API uses an asynchronous callback to return the result.

Use scenarios: Display the current version details to users, confirm the current system version status, and compare the differences between the old and new versions. For example, display the update description on the device information page, and display changes on the version history page. Use **getCurrentVersionInfo** to obtain the technical version information such as the version number and device name.

**Overview**

This API obtains the description of each component of the current version from the upgrade package management server. The process is as follows:

The description includes the function description and version features of each component. The information can be returned in **CONTENT** (text) or **URI** (link) format.

**Related methods**

- **getCurrentVersionInfo()**: obtains the current version information such as the version number and device  
name. This method can be called independently.  
- **getCurrentVersionDescription()**: obtains the description of the current version, which can be displayed to  
users.  
- The two methods can be used together. You can call **getCurrentVersionInfo** to obtain basic information and  
then call this method to obtain the detailed description for display.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | Yes | Description options. This parameter specifies the format and language of the description file. The **format** field specifies the description format (**STANDARD** or **SIMPLIFIED**). The **language** field specifies the language of the description file. The value is a string of 2 to 10 characters, for example, **zh-cn** (Chinese), **en-us** (English), and **ja-jp** (Japanese). Valid characters include letters (case sensitive) and hyphens (-). Lowercase letters are recommended. An exception is thrown if the value is out of range or contains invalid characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md)&gt;&gt; | Yes | Callback used to receive the description of the current version. The callback parameters include **err** and **info**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **info** is the current version description array, including the version description. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
// Options of the description file
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // Standard format
  language: 'zh-cn' // Chinese
};

try {
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

  // Obtain the description of the current version.
  onlineUpdater.getCurrentVersionDescription(descriptionOptions, (currentDescriptionError, info) => {
    if (currentDescriptionError) {
      console.error(`getCurrentVersionDescription error, code:${currentDescriptionError.code}, message:${currentDescriptionError.message}.`);
      return;
    }
    console.info(`getCurrentVersionDescription info ${JSON.stringify(info)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// Options of the description file
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // Standard format
  language: 'zh-cn' // Chinese
};
try {
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

  // Obtain the description of the current version.
  onlineUpdater.getCurrentVersionDescription(descriptionOptions).then((info: Array<update.ComponentDescription>) => {
    console.info(`getCurrentVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((descriptionError: BusinessError) => {
    console.error(`getCurrentVersionDescription error, code:${descriptionError.code}, message:${descriptionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise<Array<ComponentDescription>>
```

Obtains the description of the current version. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After this API is called successfully, the current version description array is returned, which can be used for version information display, version status confirmation, and version comparison and analysis. This API uses a promise to return the result.

Use scenarios: Display the current version details to users, confirm the current system version status, and compare the differences between the old and new versions. For example, display the update description on the device information page, and display changes on the version history page. Use **getCurrentVersionInfo** to obtain the technical version information such as the version number and device name.

**Overview**

This API obtains the description of each component of the current version from the upgrade package management server. The process is as follows: Read the current version ID. Send a request to the server to obtain the description. (Specify the format and language by descriptionOptions.) The server queries the description based on the version ID. Parse the description data and convert it to the target format and language. Return the description array. The description includes the function description and version features of each component. The information can be returned in **CONTENT** (text) or **URI** (link) format.

**Related methods**

- **getCurrentVersionInfo()**: obtains the current version information such as the version number and device  
name. This method can be called independently.  
- **getCurrentVersionDescription()**: obtains the description of the current version, which can be displayed to  
users.  
- The two methods can be used together. You can call **getCurrentVersionInfo** to obtain basic information and  
then call this method to obtain the detailed description for display.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | Yes | Description options. This parameter specifies the format and language of the description file. The **format** field specifies the description format (**STANDARD** or **SIMPLIFIED**). The **language** field specifies the language of the description file. The value is a string of 2 to 10 characters, for example, **zh-cn** (Chinese), **en-us** (English), and **ja-jp** (Japanese). Valid characters include letters (case sensitive) and hyphens (-). Lowercase letters are recommended. An exception is thrown if the value is out of range or contains invalid characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md)&gt;&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is the current version description array, which is used to display the current version and version comparison. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getCurrentVersionDescription](#getcurrentversiondescription)

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(callback: AsyncCallback<CurrentVersionInfo>): void
```

Obtains information about the current version. After the API is successfully called, a **CurrentVersionInfo** object is returned, including the system version number, device name, and version components. This helps users quickly learn about the device version status, facilitating upgrade decision-making and troubleshooting. This API uses an asynchronous callback to return the result.

Use scenarios: Display the system version on the settings screen, check whether the version is the latest, and perform version management and diagnosis. To display the readable description of the current version to users, you are advised to use **getCurrentVersionDescription**.

**Overview**

This method reads the current version information from the local system files and configurations of the device, including **osVersion** (system version number read from the system version configuration file), **deviceName** (device name read from the device attribute configuration), and **versionComponents** (array of component version information read from the system partition metadata). The information comes from the local device and does not depend on the network connection. After this method is called, the locally cached version data is directly returned.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[CurrentVersionInfo](arkts-basicservices-update-currentversioninfo-i-sys.md)&gt; | Yes | Callback used to receive the current version information (**CurrentVersionInfo**). The callback parameters include **err** and **currentInfo**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **currentInfo** indicates the current version information, including the **osVersion**, **deviceName**, and **versionComponents** fields. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
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

  // Obtain the current version information and obtain the version details using a callback.
  onlineUpdater.getCurrentVersionInfo((currentVersionInfoError: BusinessError,
    currentVersionInfo: update.CurrentVersionInfo) => {
    if (currentVersionInfoError) {
      console.error(`getCurrentVersionInfo error, code:${currentVersionInfoError.code}, message:${currentVersionInfoError.message}.`);
      return;
    }
    console.info(`info osVersion = ${currentVersionInfo?.osVersion}`);
    console.info(`info deviceName = ${currentVersionInfo?.deviceName}`);
    console.info(`info displayVersion = ${currentVersionInfo?.versionComponents[0].displayVersion}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Obtain the current version information.
  onlineUpdater.getCurrentVersionInfo().then((info: update.CurrentVersionInfo) => {
    console.info(`info osVersion = ${info.osVersion}`);
    console.info(`info deviceName = ${info.deviceName}`);
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
  }).catch((currentVersionInfoError: BusinessError) => {
    console.error(`getCurrentVersionInfo error, code:${currentVersionInfoError.code}, message:${currentVersionInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get updater error: ${error}`);
}
```

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(): Promise<CurrentVersionInfo>
```

Obtains information about the current version. After the API is successfully called, a **CurrentVersionInfo** object is returned, including the system version number, device name, and version components. This helps users quickly learn about the device version status, facilitating upgrade decision-making and troubleshooting. This API uses a promise to return the result.

Use scenarios: Display the system version on the settings screen, check whether the version is the latest, and perform version management and diagnosis. To display the readable description of the current version to users, you are advised to use **getCurrentVersionDescription**.

**Overview**

This method reads the current version information from the local system files and configurations of the device, including **osVersion** (system version number read from the system version configuration file), **deviceName** (device name read from the device attribute configuration), and **versionComponents** (array of component version information read from the system partition metadata). The information comes from the local device and does not depend on the network connection. After this method is called, the locally cached version data is directly returned.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CurrentVersionInfo](arkts-basicservices-update-currentversioninfo-i-sys.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is the current version information, which is used to display the system version and version comparison. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getCurrentVersionInfo](#getcurrentversioninfo)

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

Obtains the description of the new version. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After the API is successfully called, the new version description array is returned, including the version description of each component. This API uses an asynchronous callback to return the result.

Use scenarios: Display version updates to users and confirm whether to perform the upgrade. Help users understand the function improvements and fixes of the new version and make upgrade decisions.

**Overview**

This API sends requests to the upgrade package management server to query the version description of each component based on the version digest information returned by **checkNewVersion**. The description includes the function improvements, fixes, and version features of each component. The server returns a description array. Each element corresponds to the description of a component (**ComponentDescription**). The server returns the description text in the format (**STANDARD** or **SIMPLIFIED**) and language (for example, **zh-cn**) specified by **descriptionOptions**. The description can be in text format (**DescriptionType.CONTENT**) or link format (**DescriptionType.URI**) and is used to display the version updates to users.

**Calling sequence**

- You need to call **checkNewVersion** to check whether a new version is available and obtain the version digest  
information.  
- The value of **versionDigestInfo** is obtained from the result returned by calling **checkNewVersion**.  
**checkNewVersion** must be called first.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information, including the version ID (**versionDigest** field). This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API. The version digest uniquely identifies a version generated by the server and is used for subsequent version query, download, and upgrade operations. This parameter is valid only when **isExistNewVersion** is **true**. |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | Yes | Description options. This parameter specifies the format and language of the description file. The **format** field specifies the description format (**STANDARD** or **SIMPLIFIED**). The **language** field specifies the language of the description file. The value is a string of 2 to 10 characters, for example, **zh-cn** (Chinese), **en-us** (English), and **ja-jp** (Japanese). Valid characters include letters (case sensitive) and hyphens (-). Lowercase letters are recommended. An exception is thrown if the value is out of range or contains invalid characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md)&gt;&gt; | Yes | Callback used to receive the description of the new version. The callback parameters include **err** and **descriptionInfo**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **descriptionInfo** is the new version description array, including the version description of each component. Before calling this API, you must call **checkNewVersion** to check whether a new version is available. **descriptionInfo** is valid only when **isExistNewVersion** is **true**. If **isExistNewVersion** is **false**, **descriptionInfo** is **null**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the version digest information from the checkNewVersion result.
};

// Options of the description file
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // Standard format
  language: 'zh-cn' // Chinese
};

try {
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
  // Obtain the description of the new version.
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions, (descriptionError, descriptionInfo) => {
    if (descriptionError) {
      console.error(`getNewVersionDescription error, code:${descriptionError.code}, message:${descriptionError.message}.`);
      return;
    }
    console.info(`getNewVersionDescription info ${JSON.stringify(descriptionInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get updater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options of the description file
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // Standard format
  language: 'zh-cn' // Chinese
};

try {
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

  // Obtain the description of the new version.
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions)
    .then((info: Array<update.ComponentDescription>) => {
    console.info(`getNewVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((descriptionError: BusinessError) => {
    console.error(`getNewVersionDescription promise error, code:${descriptionError.code}, message:${descriptionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions
    ): Promise<Array<ComponentDescription>>
```

Obtains the description of the new version (**ComponentDescription**). This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After the API is successfully called, the new version description array is returned, including the version description of each component. This API uses a promise to return the result.

Use scenarios: Display version updates to users and confirm whether to perform the upgrade. Help users understand the function improvements and fixes of the new version and make upgrade decisions.

**Overview**

This API sends requests to the upgrade package management server to query the version description of each component based on the version digest information returned by **checkNewVersion**. The description includes the function improvements, fixes, and version features of each component. The server returns a description array. Each element corresponds to the description of a component (**ComponentDescription**). The server returns the description text in the format (**STANDARD** or **SIMPLIFIED**) and language (for example, **zh-cn**) specified by **descriptionOptions**. The description can be in text format (**DescriptionType.CONTENT**) or link format (**DescriptionType.URI**) and is used to display the version updates to users.

**Calling sequence**

- You need to call **checkNewVersion** to check whether a new version is available and obtain the version digest  
information.  
- The value of **versionDigestInfo** is obtained from the result returned by calling **checkNewVersion**.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | Yes | Description options. This parameter specifies the format and language of the description file. The **format** field specifies the description format (**STANDARD** or **SIMPLIFIED**). The **language** field specifies the language of the description file. The value is a string of 2 to 10 characters, for example, **zh-cn** (Chinese), **en-us** (English), and **ja-jp** (Japanese). Valid characters include letters (case sensitive) and hyphens (-). Lowercase letters are recommended. An exception is thrown if the value is out of range or contains invalid characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ComponentDescription](arkts-basicservices-update-componentdescription-i-sys.md)&gt;&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is the new version description array, which is used to display the version updates to the user and confirm the updates. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getNewVersionDescription](#getnewversiondescription)

## getNewVersionInfo

```TypeScript
getNewVersionInfo(callback: AsyncCallback<NewVersionInfo>): void
```

Obtains the new version information and sends requests to the upgrade package management server to query the detailed information about the new version, including the version number, version digest information, and version components. After the API is successfully called, a **NewVersionInfo** object is returned, containing complete version information, including the version digest information and version components. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This API uses an asynchronous callback to return the result.

Use scenarios: The technical information (such as the version number, upgrade package size, and component details) of the new version is required for version management, diagnosis, or technical analysis. This API helps developers fully understand the technical details of the new version.

To display readable version description to users, you are advised to use the **getNewVersionDescription** method.

**Overview**

This API sends requests to the upgrade package management server to query the complete details of the new version based on the version digest information returned by **checkNewVersion**. The server returns a **NewVersionInfo** object, including **versionDigestInfo** (version digest information used as the version ID for subsequent download and upgrade operations) and a **versionComponents** array (version number, size, and type of each component). This API can be called only when the value of **isExistNewVersion** is **true** by calling **checkNewVersion**. Otherwise, empty data is returned.

**Calling sequence**

- You must first call **checkNewVersion** to check whether a new version is available.  
- This API can be called only when the value of **isExistNewVersion** is **true**.

**Related methods**

- **checkNewVersion()**: checks whether a new version is available (prerequisite method).  
- **getNewVersionInfo()**: obtains the technical information (version number and component details) of the new  
version, which is applicable to version management and diagnosis scenarios.  
- **getNewVersionDescription()**: obtains the description of the new version, which is used to display the  
updated content to users.  
- **download()**: downloads the upgrade package (subsequent method).

**Constraints**

- This method provides the online upgrade function, which depends on the upgrade package management server  
deployed by the vendor.  
- You must first call **checkNewVersion** to check whether a new version is available. This API can be called  
only when **isExistNewVersion** is **true**.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md)&gt; | Yes | Callback used to receive the new version information (**NewVersionInfo**). The callback parameters include **err** and **newInfo**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. Before calling this API, you must call **checkNewVersion** to check whether a new version is available. **newInfo** is valid only when **isExistNewVersion** is **true**. If **isExistNewVersion** is **false**, **newInfo** is **null**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Obtain the new version information and obtain the version details using a callback.
  onlineUpdater.getNewVersionInfo((getNewVersionInfoError: BusinessError, newInfo: update.NewVersionInfo) => {
    if (getNewVersionInfoError) {
      console.error(`getNewVersionInfo error, code:${getNewVersionInfoError.code}, message:${getNewVersionInfoError.message}.`);
      return;
    }
    console.info(`info displayVersion = ${newInfo?.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${newInfo?.versionComponents[0].innerVersion}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Obtain new version information.
  onlineUpdater.getNewVersionInfo().then((info: update.NewVersionInfo) => {
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${info.versionComponents[0].innerVersion}`);
  }).catch((getNewVersionInfoError: BusinessError) => {
    console.error(`getNewVersionInfo promise error, code:${getNewVersionInfoError.code}, message:${getNewVersionInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## getNewVersionInfo

```TypeScript
getNewVersionInfo(): Promise<NewVersionInfo>
```

Obtains the new version information and sends requests to the upgrade package management server to query the detailed information about the new version, including the version number, version digest information, and version components. After the API is successfully called, a **NewVersionInfo** object is returned, containing complete version information, including the version digest information and version components. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This API uses a promise to return the result.

Use scenarios: The technical information (such as the version number, upgrade package size, and component details) of the new version is required for version management, diagnosis, or technical analysis. This API helps developers fully understand the technical details of the new version.

To display readable version description to users, you are advised to use the **getNewVersionDescription** method.

**Overview**

This API sends requests to the upgrade package management server to query the complete details of the new version based on the version digest information returned by **checkNewVersion**. The server returns a **NewVersionInfo** object, including **versionDigestInfo** (version digest information used as the version ID for subsequent download and upgrade operations) and a **versionComponents** array (version number, size, and type of each component). This API can be called only when the value of **isExistNewVersion** is **true** by calling **checkNewVersion**. Otherwise, empty data is returned.

**Calling sequence**

- You must first call **checkNewVersion** to check whether a new version is available.  
- This API can be called to obtain details about the new version only when the value of **isExistNewVersion** is  
**true** by calling **checkNewVersion**.

**Related methods**

- **checkNewVersion()**: checks whether a new version is available (prerequisite method).  
- **getNewVersionInfo()**: obtains the technical information (version number and component details) of the new  
version, which is applicable to version management and diagnosis scenarios.  
- **getNewVersionDescription()**: obtains the description of the new version, which is used to display the  
updated content to users.  
- **download()**: downloads the upgrade package (subsequent method).

**Constraints**

- This method provides the online upgrade function, which depends on the upgrade package management server  
deployed by the vendor.  
- You must first call **checkNewVersion** to check whether a new version is available. This API can be called  
only when **isExistNewVersion** is **true**.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NewVersionInfo](arkts-basicservices-update-newversioninfo-i-sys.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is the detailed information about the new version. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getNewVersionInfo](#getnewversioninfo)

## getTaskInfo

```TypeScript
getTaskInfo(callback: AsyncCallback<TaskInfo>): void
```

Obtains information about the update task. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After the information is obtained, a **TaskInfo** object is returned, including whether the task exists, task status, and progress. This helps you monitor the upgrade progress in real time, detect exceptions promptly, and optimize the upgrade policy, improving the controllability and success rate of the upgrade process. This API uses an asynchronous callback to return the result.

Use scenarios: Track the upgrade progress in real time, monitor the task status, and detect exceptions promptly.

**Overview**

This method queries the status of the current upgrade task from the system upgrade service. The system maintains an upgrade task status record, including **existTask** (whether a task exists) and **taskBody** (task details, including the version digest, current status, progress percentage, and installation mode). The task status is updated in real time during the download and installation processes. This method can be used to query the latest status. The status information is stored in the memory of the system service process. Each time this method is called, the status information is queried from the service process and returned in real time.

**Related methods**

- **download()**: downloads the upgrade package. (You can call **getTaskInfo** to query the download progress and  
status during download.)  
- **upgrade()**: installs the upgrade package. (You can call **getTaskInfo** to query the installation progress  
and status during installation.)  
- **pauseDownload()**: pauses download. (You can call **getTaskInfo** to query the pause status after download is  
paused.)  
- **terminateUpgrade()**: terminates upgrade. (You can call **getTaskInfo** to query the task cancellation status  
after upgrade is terminated.)

**When to Call:**

- You are advised to call **getTaskInfo** to query the task progress as required after calling **download** or  
**upgrade** to start the upgrade task.  
- During upgrade, you can obtain the progress in real time using an event listener registered by **on** or use  
**getTaskInfo** to query the current status.  
- In the case of an exception or interruption, you can call **getTaskInfo** to confirm the task status and  
determine the follow-up procedure.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | Yes | Callback used to receive the upgrade task information (**TaskInfo**). The callback parameters include **err** and **taskInfo**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **taskInfo** indicates the upgrade task information, including the **existTask** and **taskBody** fields. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
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

  // Obtain the update task information and use a callback to receive the task status.
  onlineUpdater.getTaskInfo((taskInfoError: BusinessError, taskInfo: update.TaskInfo) => {
    if (taskInfoError) {
      console.error(`getTaskInfo error, code:${taskInfoError.code}, message:${taskInfoError.message}.`);
      return;
    }
    console.info(`getTaskInfo existTask= ${taskInfo?.existTask}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
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
  // Obtain information about the update task.
  onlineUpdater.getTaskInfo().then((info: update.TaskInfo) => {
    console.info(`getTaskInfo existTask= ${info.existTask}`);
  }).catch((taskInfoError: BusinessError) => {
    // Handle the failure of obtaining the task information.
    console.error(`Failed to get task info. code:${taskInfoError.code}, message:${taskInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## getTaskInfo

```TypeScript
getTaskInfo(): Promise<TaskInfo>
```

Obtains information about the update task. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After the information is obtained, a **TaskInfo** object is returned, including whether the task exists, task status, and progress. This helps you monitor the upgrade progress in real time, detect exceptions promptly, and optimize the upgrade policy, improving the controllability and success rate of the upgrade process. This API uses a promise to return the result.

Use scenarios: Track the upgrade progress in real time, monitor the task status, and detect exceptions promptly.

**Overview**

This method queries the status of the current upgrade task from the system upgrade service. The system maintains an upgrade task status record, including **existTask** (whether a task exists) and **taskBody** (task details, including the version digest, current status, progress percentage, and installation mode). The task status is updated in real time during the download and installation processes. This method can be used to query the latest status. The status information is stored in the memory of the system service process. Each time this method is called, the status information is queried from the service process and returned in real time.

**Related methods**

- **download()**: downloads the upgrade package. (You can call **getTaskInfo** to query the download progress and  
status during download.)  
- **upgrade()**: installs the upgrade package. (You can call **getTaskInfo** to query the installation progress  
and status during installation.)  
- **pauseDownload()**: pauses download. (You can call **getTaskInfo** to query the pause status after download is  
paused.)  
- **terminateUpgrade()**: terminates upgrade. (You can call **getTaskInfo** to query the task cancellation status  
after upgrade is terminated.)

**When to Call:**

- You are advised to call **getTaskInfo** to query the task progress periodically after calling **download** or  
**upgrade** to start the upgrade task.  
- During upgrade, you can obtain the progress in real time using an event listener registered by **on** or use  
**getTaskInfo** to query the current status.  
- In the case of an exception or interruption, you can call **getTaskInfo** to confirm the task status and  
determine the follow-up procedure.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TaskInfo](arkts-basicservices-agent-taskinfo-i.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is a **TaskInfo** object, which is used to query and monitor the upgrade task status. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getTaskInfo](#gettaskinfo)

## getUpgradePolicy

```TypeScript
getUpgradePolicy(callback: AsyncCallback<UpgradePolicy>): void
```

Obtains the upgrade policy. If this API is called successfully, an **UpgradePolicy** object is returned, containing the configuration of the automatic download policy, automatic upgrade policy, and upgrade time period. This API uses an asynchronous callback to return the result.

Use scenarios: The device management system checks the current upgrade policy configuration, the OTA upgrade client checks the policy configuration before startup, and the enterprise device management platform displays the upgrade rules.

**Overview**

This method queries the upgrade policy configuration from the system upgrade service. The policy configuration is stored in the system configuration file, including **downloadStrategy** (automatic download switch), **autoUpgradeStrategy** (automatic upgrade switch), and **autoUpgradePeriods** (upgrade period). When this method is called, the system service reads the configuration file, parses the policy parameters, encapsulates them into an **UpgradePolicy** object, and returns the object. The upgrade policy is set using **setUpgradePolicy**. The policy is persistently stored in the system, which remains valid after the device is restarted.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md)&gt; | Yes | Callback used to receive the upgrade policy. The callback parameters include **err** and **policy**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. **policy** includes the **downloadStrategy**, **autoUpgradeStrategy**, and **autoUpgradePeriods** fields. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Obtain the upgrade policy and use a callback to receive the policy configuration.
  onlineUpdater.getUpgradePolicy((upgradePolicyError: BusinessError, policy: update.UpgradePolicy) => {
    if (upgradePolicyError) {
      console.error(`getUpgradePolicy error. code:${upgradePolicyError.code}, message:${upgradePolicyError.message}.`);
      return;
    }
    console.info(`policy downloadStrategy = ${policy?.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy?.autoUpgradeStrategy}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Obtain the upgrade policy.
  onlineUpdater.getUpgradePolicy().then((policy: update.UpgradePolicy) => {
    console.info(`policy downloadStrategy = ${policy.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy.autoUpgradeStrategy}`);
  }).catch((upgradePolicyError: BusinessError) => {
    console.error(`getUpgradePolicy error. code:${upgradePolicyError.code}, message:${upgradePolicyError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## getUpgradePolicy

```TypeScript
getUpgradePolicy(): Promise<UpgradePolicy>
```

Obtains the upgrade policy. If this API is called successfully, an **UpgradePolicy** object is returned, containing the configuration of the automatic download policy, automatic upgrade policy, and upgrade time period. This API uses a promise to return the result.

Use scenarios: The device management system checks the current upgrade policy configuration, the OTA upgrade client checks the policy configuration before startup, and the enterprise device management platform displays the upgrade rules.

**Overview**

This method queries the upgrade policy configuration from the system upgrade service. The policy configuration is stored in the system configuration file, including **downloadStrategy** (automatic download switch), **autoUpgradeStrategy** (automatic upgrade switch), and **autoUpgradePeriods** (upgrade period). When this method is called, the system service reads the configuration file, parses the policy parameters, encapsulates them into an **UpgradePolicy** object, and returns the object. The upgrade policy is set using **setUpgradePolicy**. The policy is persistently stored in the system, which remains valid after the device is restarted.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md)&gt; | Promise used to return the result. If the operation is successful, the return value of **resolve** is an **UpgradePolicy** object, which is used to query the policy configuration such as automatic download, automatic upgrade, and upgrade periods. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [getUpgradePolicy](#getupgradepolicy)

## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

Disables listening for update events. After the API is successfully called, the listener for the upgrade events of the corresponding type is unregistered. No more notifications for this event type will be received, preventing memory leak.

Use scenarios: The upgrade process is complete and the upgrade event does not need to be monitored. You must use **on()** to register a listener before using this method to unregister the listener.

**Overview**

The process is as follows: Confirm the event type based on **eventClassifyInfo**. Remove the corresponding callback from the event listening list of the upgrade service. (If **taskCallback** is passed, remove the specific callback; otherwise, remove all listeners for the event type.) Release the system resources occupied by the listener. Disconnect the event transfer channel. After the listener is unregistered, the update service no longer sends event notifications of this type to the app, and the app process no longer receives related event callbacks. The memory and IPC channel occupied by the listener are released.

**API called in pairs**

- This API must be used in pairs with **on()** to unregister a registered event listener.  
- This API can be called only after a listener is registered using **on()**.  
- You are advised to call this method after the upgrade process is complete or when the page is destroyed to  
release resources in a timely manner.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | Yes | **EventClassifyInfo** object, which is used to specify the type of the upgrade event whose listener needs to be unregistered. The prerequisite is that you have registered a listener by calling **on**. After the listener is registered, the system maintains the event listening list and continuously receives local update event notifications of the corresponding type. After this parameter is used to unregister the listener, the system removes the corresponding listening record from the event listening list, and releases the memory and IPC channel occupied by the listener. The app will no longer receive event notifications of this type. |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | No | Task callback, which is used to process upgrade tasks. Callback signature. In the signature, **eventInfo** is an **EventInfo** object, whose value is **void**. **eventInfo** contains the **eventId** (event ID) and **taskBody** (task data) fields. Pass this parameter when a specific callback listener needs to be unregistered. If this parameter is not passed, all listeners for the event type are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // Task event type
  extraInfo: ''
};
try {
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
  // Unregister the event listener.
  onlineUpdater.off(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`onlineUpdater off ${JSON.stringify(eventInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

Registers an event listener to monitor the upgrade status in real time. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. After the API is successfully called, the upgrade event of the corresponding type is listened for. When an event occurs, the event information is transferred using a callback, including the event ID, task status, and progress.

Use scenarios: Display the upgrade progress bar and percentage on the OTA upgrade client, monitor the batch device upgrade status in the device management system, and track the progress of automatic upgrade in the background.

**Overview**

This method registers an upgrade event listener. The process is as follows: Construct **eventClassifyInfo** to specify the event type, for example, **TASK**. Register the callback function with the event listening list of the upgrade service. The upgrade service triggers an event upon status changes, for example, when the download starts, the download progress is updated, or the upgrade succeeds. The event is transferred to the app process through the IPC channel. Call the registered callback to transfer the **EventInfo** object. This API uses an asynchronous callback to return the result, which does not affect the upgrade process. You are advised to call **off** to unregister the listener after the upgrade process is complete to prevent memory leak.

**API called in pairs**

- After a listener is registered by calling **on()**, you are advised to call **off()** to unregister the  
listener when it is no longer needed.  
- If **off()** is not called to unregister the listener, memory leak occurs, affecting system performance.  
- You are advised to call **off()** after the upgrade process is complete or when the page is destroyed.

**Suggestions**

- Register a listener before performing long-time operations such as calling **download** or **upgrade**.  
- Unregister the listener after the operation is complete or the final event (such as **EVENT_DOWNLOAD_SUCCESS**  
or **EVENT_UPGRADE_SUCCESS**) is received.

**Related methods**

- **off()**: unregisters the event listener. This API is used with **on()** in pairs.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | Yes | **EventClassifyInfo** object, which is used to specify the type of the upgrade event to be listened for. The system registers an upgrade event listener of the corresponding type based on **eventClassifyInfo**. When an event occurs, the event information is transferred through **taskCallback**. |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | Yes | Task callback, which is used to process upgrade tasks. Callback signature. In the signature, **eventInfo** is an **EventInfo** object, whose value is **void**. **eventInfo** contains the **eventId** (event ID) and **taskBody** (task data) fields. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // Task event type
  extraInfo: '' // Additional information. If this parameter is left empty, no additional information is available.
};
try {
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
  // Register an event listener to monitor the update status in real time.
  onlineUpdater.on(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`updater on ${JSON.stringify(eventInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## pauseDownload

```TypeScript
pauseDownload(
      versionDigestInfo: VersionDigestInfo,
      pauseDownloadOptions: PauseDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

Pauses download of the new version. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This method can be called to pause the download only when there is an ongoing download task. After the download is paused, call **resumeDownload()** to resume the download. After the download is resumed, call **upgrade()** to install the upgrade package. This API uses an asynchronous callback to return the result.

Use scenarios: The user proactively pauses the download, the network connection is poor, or the download needs to be paused during a specific period (for example, 22:00-06:00 at night or 08:00-18:00 on workdays).

**Overview**

The process is as follows: Disconnect from the network. Save the progress status, including the number of downloaded bytes, file path, network type, and version digest information. Mark the task status as **DOWNLOAD_PAUSED**. Release some network resources. When the download is paused, the system writes the progress status for persistent storage so that the download can be resumed after the device is rebooted or the app is exited. Based on the **isAllowAutoResume** parameter, the system may automatically resume the download or wait for the download to be resumed manually by calling **resumeDownload**.

**API called in pairs**

- This API must be used in pairs with **resumeDownload()** to pause and resume the download process. After the  
download is paused, call **resumeDownload()** to resume the download.

**State transition description**

- After the download is paused, you can call **resumeDownload()** to resume the download.  
- After the download is paused, you can call **getTaskInfo()** to query the current task status.  
- After the download is paused, you cannot directly call **upgrade()** to install the upgrade package. You must  
resume the download and complete the installation first.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| pauseDownloadOptions | [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | Yes | Pausing download options, which are used to control the pause behavior. If there is no ongoing download task, using this parameter will cause the pause operation to fail or the parameter to be invalid. The **isAllowAutoResume** field specifies whether to allow automatically resuming the download. You are advised to set this parameter to **true** when the network is unstable, improving the download success rate. You are advised to set this parameter to **false** when the download time needs to be precisely controlled or resuming download needs to be prevented in specific network environments. In this case, you can call **resumeDownload** to control when to resume the download. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the download pause result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for pausing download
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // Whether to allow automatic resuming of download
};
try {
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
  // Pause the download of the upgrade package.
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions,
    (pauseDownloadError: BusinessError) => {
    if (pauseDownloadError) {
      console.error(`pauseDownload error. code:${pauseDownloadError.code}, message:${pauseDownloadError.message}.`);
    } else {
      console.info(`pauseDownload success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for pausing download
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // Whether to allow automatic resuming of download
};
try {
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
  // Pause the download of the upgrade package.
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions).then(() => {
    console.info(`pauseDownload`);
  }).catch((pauseDownloadError: BusinessError) => {
    console.error(`pauseDownload error. code:${pauseDownloadError.code}, message:${pauseDownloadError.message}.`);
    
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## pauseDownload

```TypeScript
pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise<void>
```

Pauses download of the new version. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This method can be called to pause the download only when there is an ongoing download task. After the download is paused, call **resumeDownload()** to resume the download. After the download is resumed, call **upgrade()** to install the upgrade package. This API uses a promise to return the result.

Use scenarios: The user proactively pauses the download, the network connection is poor, or the download needs to be performed during a specific period.

**Overview**

The process is as follows: Disconnect from the network. Save the progress status, including the number of downloaded bytes, file path, network type, and version digest information. Mark the task status as **DOWNLOAD_PAUSED**. Release some network resources. When the download is paused, the system writes the progress status for persistent storage so that the download can be resumed after the device is rebooted or the app is exited. Based on the **isAllowAutoResume** parameter, the system may automatically resume the download or wait for the download to be resumed manually by calling **resumeDownload**.

**API called in pairs**

- This API must be used in pairs with **resumeDownload()** to pause and resume the download process. After the  
download is paused, call **resumeDownload()** to resume the download.

**State transition description**

- After the download is paused, you can call **resumeDownload()** to resume the download.  
- After the download is paused, you can call **getTaskInfo()** to query the current task status.  
- After the download is paused, you cannot directly call **upgrade()** to install the upgrade package. You must  
resume the download and complete the installation first.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| pauseDownloadOptions | [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | Yes | Pausing download options, which are used to control the pause behavior. This parameter takes effect only when there is an ongoing download task. If there is no ongoing download task, using this parameter will cause the pause operation to fail or the parameter to be invalid. The **isAllowAutoResume** field specifies whether to allow automatically resuming the download. You are advised to set this parameter to **true** when the network is unstable, improving the download success rate. You are advised to set this parameter to **false** when the download time needs to be precisely controlled or resuming download needs to be prevented in specific network environments. In this case, you can call **resumeDownload** to control when to resume the download. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [pauseDownload](#pausedownload)

## resumeDownload

```TypeScript
resumeDownload(
      versionDigestInfo: VersionDigestInfo,
      resumeDownloadOptions: ResumeDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

Resumes a paused download task for the upgrade package, which can prevent repeatedly downloading the completed part. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This API uses an asynchronous callback to return the result.

Use scenarios: Resume download after network interruption, resume download after the user pauses it, and resume a download task in the background.

**Overview**

The process is as follows: Read the progress status saved when the download is paused (including the number of downloaded bytes, file path, and network connection). Select the network type based on **resumeDownloadOptions**. Send a request to the server to resume download (carrying the number of downloaded bytes). The server returns the remaining data. Continue writing data to the local file from the breakpoint. Update the progress in real time. When resuming the download, the system verifies the integrity of the downloaded part to ensure data consistency before continuing to receive new data.

**API called in pairs**

- This API must be used in pairs with **pauseDownload()** to pause and resume the download process.  
- This API can be called to resume download only after **pauseDownload()** is called to pause download.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| resumeDownloadOptions | [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | Yes | Resuming download options, which are used to specify the network type for resuming download. This parameter takes effect only after the **pauseDownload** API is called to pause download. If **pauseDownload** is not called to pause download, using this parameter will cause the download resumption to fail or the parameter to be invalid. The **allowNetwork** field specifies the network type allowed for resuming download. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package exceeds 100 MB, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the download resumption result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for resuming download
const resumeDownloadOptions: update.ResumeDownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // Whether to allow download over data network
};
try {
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
  // Resume the download of the upgrade package.
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions,
    (resumeDownloadError: BusinessError) => {
    if (resumeDownloadError) {
      console.error(`resumeDownload error. code:${resumeDownloadError.code}, message:${resumeDownloadError.message}.`);
    } else {
      console.info(`resumeDownload success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Options for resuming download
const resumeDownloadOptions: update.ResumeDownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // Whether to allow download over data network
};
try {
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
  // Resume the download of the upgrade package.
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions).then(() => {
    console.info(`resumeDownload start`);
  }).catch((resumeDownloadError: BusinessError) => {
    console.error(`resumeDownload error. code:${resumeDownloadError.code}, message:${resumeDownloadError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## resumeDownload

```TypeScript
resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise<void>
```

Resumes a paused download task for the upgrade package, which can prevent repeatedly downloading the completed part. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. This API uses a promise to return the result.

Use scenarios: Resume download after network interruption, resume download after the user pauses it, and resume a download task in the background.

**Overview**

The process is as follows: Read the progress status saved when the download is paused (including the number of downloaded bytes, file path, and network connection). Select the network type based on **resumeDownloadOptions**. Send a request to the server to resume download (carrying the number of downloaded bytes). The server returns the remaining data. Continue writing data to the local file from the breakpoint. Update the progress in real time. When resuming the download, the system verifies the integrity of the downloaded part to ensure data consistency before continuing to receive new data.

**API called in pairs**

- This API must be used in pairs with **pauseDownload()** to pause and resume the download process.  
- This API can be called to resume download only after **pauseDownload()** is called to pause download.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| resumeDownloadOptions | [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | Yes | Resuming download options, which are used to specify the network type for resuming download. This parameter takes effect only after the **pauseDownload** API is called to pause download. If **pauseDownload** is not called to pause download, using this parameter will cause the download resumption to fail or the parameter to be invalid. The **allowNetwork** field specifies the network type allowed for resuming download. You are advised to select a network type based on the upgrade package size and network environment. If the upgrade package exceeds 100 MB, you are advised to set the network type to **WIFI** to reduce mobile data usage and improve the download speed. If you are in a mobile scenario or there is no Wi-Fi available, you can set the network type to **CELLULAR**. If the network environment is uncertain, you are advised to set the network type to **CELLULAR_AND_WIFI**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [resumeDownload](#resumedownload)

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback<void>): void
```

Sets the upgrade policy to control the upgrade behavior. After the API is called successfully, the new upgrade policy takes effect immediately. The system controls the automatic download, automatic upgrade, and upgrade periods based on the policy. This API uses an asynchronous callback to return the result.

Use scenarios: enterprise device management, upgrade period configuration and automatic download control. This method helps users flexibly configure upgrade behaviors to meet enterprise management and customization requirements.

**Overview**

This method writes the upgrade policy to the system configuration file and updates the running parameters of the upgrade service.

The process is as follows: Verify the validity of the policy parameters. Write the policy data to the system configuration file for persistent storage. Update the policy cache of the upgrade service. Notify the upgrade service to apply the new policy. The policy takes effect immediately. The system determines whether to automatically download the upgrade package based on **downloadStrategy**, whether to automatically install the upgrade package based on **autoUpgradeStrategy**, and the upgrade period based on **autoUpgradePeriods**. The policy is stored permanently. After the device is restarted, the policy is still valid.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | Yes | Upgrade policy, which is used to control the upgrade behavior. This parameter includes the **downloadStrategy** (automatic download policy), **autoUpgradeStrategy** (automatic upgrade policy), and **autoUpgradePeriods** (automatic upgrade period) fields. **downloadStrategy** specifies whether automatic download is allowed. The value **true** indicates that automatic download is allowed (applicable to scenarios where the system automatically detects and downloads the new version), and the value **false** indicates that automatic download is not allowed (applicable to scenarios where users need to manually confirm the download). **autoUpgradeStrategy** specifies whether automatic upgrade is allowed. The value **true** indicates that automatic upgrade is allowed (applicable to the scenario where the system needs to automatically complete the upgrade process), and the value **false** indicates that automatic upgrade is not allowed (applicable to the scenario where users need to manually confirm the upgrade). **autoUpgradePeriods** specifies the automatic upgrade period (optional). Pass this parameter when automatic upgrade needs to be performed in a specified period, for example, at night. If this parameter is not passed, the default value is an empty array **[]**, indicating that the automatic upgrade period is not specified. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the upgrade policy configuration result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // Disable automatic download.
  autoUpgradeStrategy: false, // Disable automatic upgrade.
  autoUpgradePeriods: [ { start: 120, end: 240 }] // Automatic upgrade period, in minutes
};
try {
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
  // Set the upgrade policy and use a call back to return the result.
  onlineUpdater.setUpgradePolicy(upgradePolicy, (setUpgradePolicyError: BusinessError) => {
    if (setUpgradePolicyError) {
      console.error(`setUpgradePolicy error, code:${setUpgradePolicyError.code}, message:${setUpgradePolicyError.message}.`);
    } else {
      console.info(`setUpgradePolicy success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // Disable automatic download.
  autoUpgradeStrategy: false, // Disable automatic upgrade.
  autoUpgradePeriods: [ { start: 120, end: 240 }] // Automatic upgrade period, in minutes
};
try {
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
  // Set the upgrade policy.
  onlineUpdater.setUpgradePolicy(upgradePolicy).then(() => {
    console.info(`setUpgradePolicy success`);
  }).catch((setUpgradePolicyError: BusinessError) => {
    console.error(`setUpgradePolicy promise error, code:${setUpgradePolicyError.code}, message:${setUpgradePolicyError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy): Promise<void>
```

Sets the upgrade policy to control the upgrade behavior. After the API is called successfully, the new upgrade policy takes effect immediately. The system controls the automatic download, automatic upgrade, and upgrade periods based on the policy. This API uses a promise to return the result.

Use scenarios: enterprise device management, upgrade period configuration and automatic download control. This method helps users flexibly configure upgrade behaviors to meet enterprise management and customization requirements.

**Overview**

This method writes the upgrade policy to the system configuration file and updates the running parameters of the upgrade service.

The process is as follows: Verify the validity of the policy parameters. Write the policy data to the system configuration file for persistent storage. Update the policy cache of the upgrade service. Notify the upgrade service to apply the new policy. The policy takes effect immediately. The system determines whether to automatically download the upgrade package based on **downloadStrategy**, whether to automatically install the upgrade package based on **autoUpgradeStrategy**, and the upgrade period based on **autoUpgradePeriods**. The policy is stored permanently. After the device is restarted, the policy is still valid.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| policy | [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | Yes | Upgrade policy, which is used to control the upgrade behavior. This parameter includes the **downloadStrategy** (automatic download policy), **autoUpgradeStrategy** (automatic upgrade policy), and **autoUpgradePeriods** (automatic upgrade period) fields. **downloadStrategy** specifies whether automatic download is allowed. The value **true** indicates that automatic download is allowed (applicable to scenarios where the system automatically detects and downloads the new version), and the value **false** indicates that automatic download is not allowed (applicable to scenarios where users need to manually confirm the download). **autoUpgradeStrategy** specifies whether automatic upgrade is allowed. The value **true** indicates that automatic upgrade is allowed (applicable to the scenario where the system needs to automatically complete the upgrade process), and the value **false** indicates that automatic upgrade is not allowed (applicable to the scenario where users need to manually confirm the upgrade). **autoUpgradePeriods** specifies the automatic upgrade period (optional). Pass this parameter when automatic upgrade needs to be performed in a specified period, for example, at night. If this parameter is not passed, the default value is an empty array **[]**, indicating that the automatic upgrade period is not specified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value, indicating that the upgrade policy is set successfully. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [setUpgradePolicy](#setupgradepolicy)

## terminateUpgrade

```TypeScript
terminateUpgrade(callback: AsyncCallback<void>): void
```

Terminates the current upgrade task and cancels the ongoing installation. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. If the API is called successfully, the task status changes to canceled. This API uses an asynchronous callback to return the result.

Use scenarios: The user cancels the upgrade or stops the upgrade urgently. This method helps users flexibly control the upgrade process, which can prevent unnecessary upgrade or stop the upgrade in emergencies.

**Overview**

The process is as follows: Check the current task status, and only download or installation can be terminated. Send a termination command to the upgrade service. Interrupt the current operation, stop download, or stop installation. Change the task status to canceled. Clear temporary resources, disconnect from the network, and clear temporary files. Notify the upgrade service to update the status. After the upgrade is terminated, the system retains some downloaded data. You are advised to call **clearError** to clear errors and then restart the upgrade process.

**State transition description**

- This method can be called to terminate the upgrade only during the download or installation process.  
- After the task is terminated, the task status changes to canceled.  
- After the task is terminated, you can call **getTaskInfo** to query the current task status.  
- If you need to perform the upgrade again after the upgrade is terminated, you are advised to call  
**clearError** to clear errors and restart the upgrade.

**Related methods**

- **download()**\/**upgrade()**: method that can be terminated.  
- **getTaskInfo()**: queries the task status.  
- **clearError()**: clears errors. Call this API if the upgrade needs to be restarted.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the result of terminating upgrade. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Terminate the upgrade and use a callback to return the result.
  onlineUpdater.terminateUpgrade((terminateUpgradeError: BusinessError) => {
    if (terminateUpgradeError) {
      console.error(`terminateUpgrade error, code:${terminateUpgradeError.code}, message:${terminateUpgradeError.message}.`);
    } else {
      console.info(`terminateUpgrade success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
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
  // Terminate the upgrade task.
  onlineUpdater.terminateUpgrade().then(() => {
    console.info(`terminateUpgrade success`);
  }).catch((terminateUpgradeError: BusinessError) => {
    console.error(`terminateUpgrade error, code:${terminateUpgradeError.code}, message:${terminateUpgradeError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## terminateUpgrade

```TypeScript
terminateUpgrade(): Promise<void>
```

Terminates the current upgrade task and cancels the ongoing installation. This method provides the online upgrade function, which depends on the upgrade package management server deployed by the vendor. If the API is called successfully, the task status changes to canceled. This API uses a promise to return the result.

Use scenarios: The user cancels the upgrade or stops the upgrade urgently. This method helps users flexibly control the upgrade process, which can prevent unnecessary upgrade or stop the upgrade in emergencies.

**Overview**

The process is as follows: Check the current task status, and only download or installation can be terminated. Send a termination command to the upgrade service. Interrupt the current operation, stop download, or stop installation. Change the task status to canceled. Clear temporary resources, disconnect from the network, and clear temporary files. Notify the upgrade service to update the status. After the upgrade is terminated, the system retains some downloaded data. You are advised to call **clearError** to clear errors and then restart the upgrade process.

**State transition description**

- This method can be called to terminate the upgrade only during the download or installation process.  
- After the task is terminated, the task status changes to canceled.  
- After the task is terminated, you can call **getTaskInfo** to query the current task status.  
- If you need to perform the upgrade again after the upgrade is terminated, you are advised to call  
**clearError** to clear errors and restart the upgrade.

**Related methods**

- **download()**\/**upgrade()**: method that can be terminated.  
- **getTaskInfo()**: queries the task status.  
- **clearError()**: clears errors. Call this API if the upgrade needs to be restarted.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [terminateUpgrade](#terminateupgrade)

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback<void>): void
```

Upgrades the version by installing the upgrade package. After the API is successfully called, the system starts to install the upgrade package and prepares for restart to apply the new version. This API uses an asynchronous callback to return the result.

Use scenarios: Install the new version after the upgrade package is downloaded. Help users update the system version, obtain new functions, and optimize performance.

**Overview**

This method installs the downloaded upgrade package and applies it to the system. The installation process is as follows: Verify the integrity of the upgrade package. Decompress the upgrade package. Write the package to the system partition (overwriting or updating system files). Update the version ID. Prepare for the restart. Select the upgrade type based on the **upgradeOptions.order** parameter. The options are as follows: **DOWNLOAD** (download the upgrade package without installing it), **INSTALL** (install the downloaded upgrade package without automatically restarting the system), **DOWNLOAD_AND_INSTALL** (download and install the upgrade package, which is the complete process), **APPLY** (apply the installed upgrade package, and the new version needs to be applied by restarting the system), and **INSTALL_AND_APPLY** (install the upgrade package and immediately restart the system).

**Dependency description**

This method is called in the installation phase of the online upgrade process. The actual installation operation is a local operation (installing the downloaded upgrade package) and does not require network connection. However, this method is usually called after **download** is called. The entire online upgrade process depends on the upgrade package management server deployed by the device vendor.

**Calling sequence**

- Before calling this method to perform upgrade, you must call **checkNewVersion** to check whether a new version  
is available first and then call **download** to download the upgrade package.

**State transition description**

- Call this method to install the upgrade package only after the download is complete.  
- During the installation process, you can call **terminateUpgrade()** to terminate the upgrade.  
- After the installation is complete, the device will restart to apply the new version.

**Failure handling**

If the **upgrade** method fails (the status is **UPGRADE_FAIL**), you must call **clearError** to clear the abnormal status before restarting the upgrade process.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| upgradeOptions | [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | Yes | Upgrade options, which are used to specify the upgrade operation type. The **order** field specifies the upgrade command, which should be set based on the upgrade status and service requirements. The options are as follows: **DOWNLOAD**: download the upgrade package, which needs to be manually installed later; **INSTALL**: install the upgrade package that has been downloaded; **DOWNLOAD_AND_INSTALL**: download and install the upgrade package, which is the complete upgrade process; **APPLY**: apply the upgrade package that has been installed by restarting device; **INSTALL_AND_APPLY**: install the upgrade package and apply it immediately by restarting the device. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the upgrade package installation result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Installation options
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // Installation command
};
try {
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
  // Install the upgrade package.
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions, (upgradeError: BusinessError) => {
    if (upgradeError) {
      console.error(`upgrade error. code:${upgradeError.code}, message:${upgradeError.message}.`);
    } else {
      console.info(`upgrade success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Version digest information. Call checkNewVersion to check for a new version and confirm the value of isExistNewVersion is true first.
// Obtain the value from the newVersionInfo.versionDigestInfo field in the returned result.
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // Obtain the actual value from the result returned by checkNewVersion.
};

// Installation options
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // Installation command
};
try {
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
  // Install the upgrade package.
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions).then(() => {
    console.info(`upgrade start`);
  }).catch((upgradeError: BusinessError) => {
    console.error(`upgrade error. code:${upgradeError.code}, message:${upgradeError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise<void>
```

Upgrades the version by installing the upgrade package. After the API is successfully called, the system starts to install the upgrade package and prepares for restart to apply the new version. This API uses a promise to return the result.

Use scenarios: Install the new version after the upgrade package is downloaded. Help users update the system version, obtain new functions, and optimize performance.

**Overview**

This method installs the downloaded upgrade package and applies it to the system. The installation process is as follows: Verify the integrity of the upgrade package. Decompress the upgrade package. Write the package to the system partition (overwriting or updating system files). Update the version ID. Prepare for the restart. Select the upgrade type based on the **upgradeOptions.order** parameter. The options are as follows: **DOWNLOAD** (download the upgrade package without installing it), **INSTALL** (install the downloaded upgrade package without automatically restarting the system), **DOWNLOAD_AND_INSTALL** (download and install the upgrade package, which is the complete process), **APPLY** (apply the installed upgrade package, and the new version needs to be applied by restarting the system), and **INSTALL_AND_APPLY** (install the upgrade package and immediately restart the system).

**Dependency description**

This method is called in the installation phase of the online upgrade process. The actual installation operation is a local operation (installing the downloaded upgrade package) and does not require network connection. However, this method is usually called after **download** is called. The entire online upgrade process depends on the upgrade package management server deployed by the device vendor.

**Calling sequence**

Before calling this method to perform upgrade, you must call **checkNewVersion** to check whether a new version is available first and then call **download** to download the upgrade package.

**State transition description**

- Call this method to install the upgrade package only after the download is complete.  
- During the installation process, you can call **terminateUpgrade()** to terminate the upgrade.  
- After the installation is complete, the device will restart to apply the new version.

**Failure handling**

If the **upgrade** method fails (the status is **UPGRADE_FAIL**), you must call **clearError** to clear the abnormal status before restarting the upgrade process.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | Yes | Version digest information. This parameter can be used only after the **checkNewVersion** API is called to check for a new version and the value of **isExistNewVersion** is **true**. The parameter value is obtained from the **newVersionInfo** field in the result returned by the **checkNewVersion** API, which identifies a specific version. This parameter is valid only when **isExistNewVersion** is **true**. |
| upgradeOptions | [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | Yes | Upgrade options, which are used to specify the upgrade operation type. The **order** field specifies the upgrade command, which should be set based on the upgrade status and service requirements. The options are as follows: **DOWNLOAD**: download the upgrade package, which needs to be manually installed later; **INSTALL**: install the upgrade package that has been downloaded; **DOWNLOAD_AND_INSTALL**: download and install the upgrade package, which is the complete upgrade process; **APPLY**: apply the upgrade package that has been installed by restarting device; **INSTALL_AND_APPLY**: install the upgrade package and apply it immediately by restarting the device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **resolve** returns no value. If the operation fails, the return value of **reject** is an error message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter verification failed. |
| [11500104](../errorcode-update.md#11500104-ipc-error) | IPC error. |

**Examples**

See [upgrade](#upgrade)
