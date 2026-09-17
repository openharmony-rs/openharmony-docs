# LocalUpdater (System API)

Defines a tool class for updating the local firmware, such as verifying the signature and integrity of the local upgrade package, installing the local upgrade package, and listening for local upgrade events.

Use scenarios: offline system upgrade, upgrade with poor network connection, and controllable upgrade.

**Benefits**

This upgrade mode applies to offline system upgrade or upgrade with poor network connection when automatic upgrade cannot be implemented. This mode does not depend on the upgrade package management server, reducing the update cost. The upgrade time can be controlled, ensuring system integrity.

**Local upgrade**

**Implementation mechanism**

- Verification mechanism: Verify that the upgrade package is officially released and has not been tampered with by  
checking the signature, integrity, and version compatibility.  
- Installation mechanism: Decompress the upgrade package and and write its content to the system partition. Prepare  
for the device restart to apply the new version.  
- Security assurance: The upgrade package must be verified first to ensure that the source is trusted before  
installation.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void
```

Installs the upgrade package. During the upgrade, the device automatically restarts. The app status needs to be saved. This API uses an asynchronous callback to return the result.

**Overview**

The process is as follows: Read the upgrade package. Decompress the upgrade package. Verify the package integrity by verifying the signature and version compatibility based on the result of **verifyUpgradePackage**. Write the package to the system partition by overwriting or updating system files. Update the version ID. Prepare the environment for restart. The device restarts to apply the new version. Maintain the task status during the installation process. You can call **on** to monitor the installation progress and status changes. After the installation is successful, the device restarts and loads the new system version. The upgrade is complete.

**Calling sequence**

- You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before calling  
this method to install the upgrade package.  
- You must call **verifyUpgradePackage** to verify the upgrade package first. Failing to do so may cause  
installation failure or system damage.  
- After the API is successfully called, the system decompresses the upgrade package, writes its content to the  
system partition, and prepares for device restart to apply the new version. An event listener can be registered to track the installation progress.  
- You can install the upgrade package to update the system version.

Use scenarios: This method is used to upgrade the system from a local storage device (such as an SD card).

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| upgradeFiles | Array&lt;[UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md)&gt; | Yes | An array of upgrade files, which is used to specify the local upgrade files to be installed. You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before using this parameter to install the upgrade package. The parameter contains the **fileType** and **filePath** fields. The value of **filePath** is a string of 1 to 255 characters. If the value is out of range, an exception is thrown, and you need to provide the path of the upgrade package. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function used to receive the result of installing the upgrade package. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

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

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA package
  filePath: '/data/local/tmp/updater.zip' // Local update package path. The user needs to download the upgrade package from the official website of the vendor or an official channel and save it to an accessible storage path of the device, for example, /data/local/tmp/updater.zip.
}];

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Install the new version.
  localUpdater.applyNewVersion(upgradeFiles, (applyNewVersionError: BusinessError) => {
    if (applyNewVersionError) {
      console.error(`applyNewVersion error, code:${applyNewVersionError.code}, message:${applyNewVersionError.message}.`);
      return;
    }
    console.info(`applyNewVersion success`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA package
  filePath: '/data/local/tmp/updater.zip' // Local update package path. The user needs to download the upgrade package from the official website of the vendor or an official channel and save it to an accessible storage path of the device, for example, /data/local/tmp/updater.zip.
}];

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Install the new version.
  localUpdater.applyNewVersion(upgradeFiles).then(() => {
    console.info(`applyNewVersion success`);
  }).catch((applyNewVersionError: BusinessError) => {
    console.error(`applyNewVersion error, code:${applyNewVersionError.code}, message:${applyNewVersionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>
```

Installs the upgrade package. During the upgrade, the device automatically restarts. The app status needs to be saved. This API uses a promise to return the result.

**Overview**

The process is as follows: Read the upgrade package. Decompress the upgrade package. Verify the package integrity by verifying the signature and version compatibility based on the result of **verifyUpgradePackage**. Write the package to the system partition by overwriting or updating system files. Update the version ID. Prepare the environment for restart. The device restarts to apply the new version. Maintain the task status during the installation process. You can call **on** to monitor the installation progress and status changes. After the installation is successful, the device restarts and loads the new system version. The upgrade is complete.

**Calling sequence**

- You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before calling  
this method to install the upgrade package.  
- You must call **verifyUpgradePackage** to verify the upgrade package first. Failing to do so may cause  
installation failure or system damage.  
- After the API is successfully called, the system decompresses the upgrade package, writes its content to the  
system partition, and prepares for device restart to apply the new version. An event listener can be registered to track the installation progress.  
- You can install the upgrade package to update the system version.

Use scenarios: This method is used to upgrade the system from a local storage device (such as an SD card).

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| upgradeFiles | Array&lt;[UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md)&gt; | Yes | An array of upgrade files, which is used to specify the local upgrade files to be installed. You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before using this parameter to install the upgrade package. The parameter contains the **fileType** and **filePath** fields. The value of **filePath** is a string of 1 to 255 characters. If the value is out of range, an exception is thrown, and you need to provide the path of the upgrade package. |

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

See [applyNewVersion](#applynewversion)

## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

Disables listening for update events. After the API is successfully called, no more notifications for the upgrade events of the corresponding type will be received, preventing memory leak.

Use scenarios: The local upgrade process is complete and the upgrade event does not need to be monitored.

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
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | Yes | **EventClassifyInfo** object, which is used to specify the type of the upgrade event whose listener needs to be unregistered. You must use **on** to register a listener before using this method to unregister the listener. |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | No | Task callback, which is used to cancel a specified callback listener. Callback signature. In the signature, **eventInfo** is an **EventInfo** object, whose value is **void**. **eventInfo** contains the **eventId** and **taskBody** fields. Pass this parameter when a specific callback listener needs to be unregistered. If this parameter is not passed, the default value is **undefined**, indicating that all listeners for the event type are canceled. |

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
// Define the callback for task updates, which is used to process the upgrade task event.
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Unregister the local upgrade event listener.
  localUpdater.off(eventClassifyInfo, onTaskUpdate);
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

Registers an event listener to monitor the upgrade status in real time. After the API is successfully called, the upgrade event of the corresponding type is listened for. When an event occurs, the event information is transferred using a callback, including the event ID, task status, and progress. The event listener can be used to obtain the upgrade progress and status changes in real time, detect and handle upgrade exceptions promptly, thereby improving user experience and the controllability of the upgrade process.

Use scenarios: Display the upgrade progress bar and percentage on the OTA upgrade client, monitor the batch device upgrade status in the device management system, and track the progress of automatic upgrade in the background.

**Overview**

This method registers a local upgrade event listener. The process is as follows: Construct **eventClassifyInfo** to specify the event type, for example, **TASK**. Register the callback function with the local event listening list of the upgrade service. The local upgrade service triggers an event upon installation status changes, for example, when the installation starts, the installation progress is updated, or the installation succeeds. The event is transferred to the app process through the IPC channel. Call the registered callback to transfer the **EventInfo** object. This API uses an asynchronous callback to return the result, which does not affect the local upgrade process. You are advised to call **off** to unregister the listener after the upgrade process is complete to prevent memory leak.

**API called in pairs**

- After a listener is registered by calling **on()**, you are advised to call **off()** to unregister the  
listener when it is no longer needed.  
- If **off()** is not called to unregister the listener, memory leak occurs, affecting system performance.  
- You are advised to call **off()** after the upgrade process is complete or when the page is destroyed.

**Suggestions**

- Register a listener before performing long-time operations such as calling **applyNewVersion**.  
- Unregister the listener after the operation is complete or the final event is received.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | Yes | **EventClassifyInfo** object, which is used to specify the type of the upgrade event to be listened for. |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | Yes | Task callback, which is used to receive upgrade task event notifications. Callback signature. In the signature, **eventInfo** is an **EventInfo** object, whose value is **void**. **eventInfo** contains the **eventId** (event ID) and **taskBody** (task data) fields. |

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
// Define the callback for task updates, which is used to process the upgrade task event.
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Register a local upgrade event listener.
  localUpdater.on(eventClassifyInfo, onTaskUpdate);
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void
```

Verifies the upgrade package, including its digital signature, file integrity, and version compatibility, to ensure that the upgrade package is officially released and has not been tampered with. If the API is called successfully and the verification is passed, the upgrade package is considered trusted and can be used for subsequent installation. If the verification fails, an error message is returned and the installation is blocked. This API uses an asynchronous callback to return the result.

Use scenarios: When a user obtains an upgrade package from a local storage device, the source needs to be verified to ensure integrity and prevent malicious packet attacks.

**Overview**

The process is as follows: Read the upgrade package and certificate file. Use the certificate to verify the digital signature of the upgrade package, including the signature algorithm, signature value, and certificate validity. Calculate the hash value of the upgrade package and compare it with the hash value in the package to verify the file integrity. Check the compatibility between the upgrade package version and the current system version. Return the verification result. Digital signature verification ensures that the upgrade package is from a trusted source signed using the official signature. Integrity verification ensures that the upgrade package has not been tampered with. Version compatibility verification ensures that the upgrade package is applicable to the current device. After the verification is successful, the upgrade package is marked as trusted and can be used in the subsequent installation process.

**Calling sequence**

- The upgrade package must be downloaded from the official website of the vendor or from an official channel to  
ensure that the source is trusted. Using update packages downloaded from non-official channels may pose security risks.  
- You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before calling  
**applyNewVersion** to install the upgrade package.  
- If you call **applyNewVersion** without verifying the upgrade package first, the installation may fail and the  
system may be damaged.  
- The upgrade package that passes the verification can be used in the subsequent installation process.

**Related methods**

- **applyNewVersion()**: installs the upgrade package. This method can be called after the verification is  
successful.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | Yes | Upgrade file, including the file type and file path, which are used to specify the local upgrade package to be verified. |
| certsFile | string | Yes | Certificate file path, which is used to verify the upgrade package signature. The certificate file must be downloaded from the official website of the vendor to ensure that the source is trusted. The value can be an absolute path or a relative path. The path length ranges from 1 to 255 characters. Only letters, digits, underscores (_), hyphens (-), dots (.), and slashes (/) are allowed. An exception is thrown if the value is out of range or contains invalid characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to receive the verification result. The callback parameter is **err**. If the operation is successful, **err** is **null**; if the operation fails, **err** is an error object. |

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

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA package
  filePath: '/data/local/tmp/updater.zip' // Local update package path. The user needs to download the upgrade package from the official website of the vendor or an official channel and save it to an accessible storage path of the device, for example, /data/local/tmp/updater.zip.
};
// certsFile is the certificate file path, which needs to be downloaded from the official website of the vendor and saved to an accessible path on the device.
const certsFile = '/path/to/certificate.cert'; // Certificate file path, which needs to be downloaded from the official website of the vendor.

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Verify the upgrade package.
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile, (verifyUpgradePackageError: BusinessError) => {
    if (verifyUpgradePackageError) {
      console.error(`verifyUpgradePackage error, code:${verifyUpgradePackageError.code}, message:${verifyUpgradePackageError.message}.`);
      return;
    }
    console.info(`verifyUpgradePackage success`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to get localUpdater. Code: ${err.code}, message: ${err.message}.`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA package
  filePath: '/data/local/tmp/updater.zip' // Local update package path. The user needs to download the upgrade package from the official website of the vendor or an official channel and save it to an accessible storage path of the device, for example, /data/local/tmp/updater.zip.
};

// certsFile is the certificate file path, which needs to be downloaded from the official website of the vendor and saved to an accessible path on the device.
const certsFile = '/path/to/certificate.cert'; // Certificate file path, which needs to be downloaded from the official website of the vendor.

try {
  // Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
  // Verify the upgrade package.
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile).then(() => {
    console.info(`verifyUpgradePackage success`);
  }).catch((verifyUpgradePackageError: BusinessError) => {
    console.error(`verifyUpgradePackage error, code:${verifyUpgradePackageError.code}, message:${verifyUpgradePackageError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>
```

Verifies the upgrade package, including its digital signature, file integrity, and version compatibility, to ensure that the upgrade package is officially released and has not been tampered with. If the API is called successfully and the verification is passed, the upgrade package is considered trusted and can be used for subsequent installation. If the verification fails, an error message is returned and the installation is blocked. This API uses a promise to return the result.

Use scenarios: When a user obtains an upgrade package from a local storage device, the source needs to be verified to ensure integrity and prevent malicious packet attacks.

**Overview**

The process is as follows: Read the upgrade package and certificate file. Use the certificate to verify the digital signature of the upgrade package, including the signature algorithm, signature value, and certificate validity. Calculate the hash value of the upgrade package and compare it with the hash value in the package to verify the file integrity. Check the compatibility between the upgrade package version and the current system version. Return the verification result. Digital signature verification ensures that the upgrade package is from a trusted source signed using the official signature. Integrity verification ensures that the upgrade package has not been tampered with. Version compatibility verification ensures that the upgrade package is applicable to the current device. After the verification is successful, the upgrade package is marked as trusted and can be used in the subsequent installation process.

**Calling sequence**

- The upgrade package must be downloaded from the official website of the vendor or from an official channel to  
ensure that the source is trusted. Using update packages downloaded from non-official channels may pose security risks.  
- You must call **verifyUpgradePackage** to verify the upgrade package and pass the verification before calling  
**applyNewVersion** to install the upgrade package.  
- If you call **applyNewVersion** without verifying the upgrade package first, the installation may fail and the  
system may be damaged.  
- The upgrade package that passes the verification can be used in the subsequent installation process.

**Since:** 9

**Required permissions:** ohos.permission.UPDATE_SYSTEM

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | Yes | Upgrade file, including the file type and file path, which are used to specify the local upgrade package to be verified. |
| certsFile | string | Yes | Certificate file path, which is used to verify the upgrade package signature. The certificate file must be downloaded from the official website of the vendor to ensure that the source is trusted. The value can be an absolute path or a relative path. The path length ranges from 1 to 255 characters. Only letters, digits, underscores (_), hyphens (-), dots (.), and slashes (/) are allowed. An exception is thrown if the value is out of range or contains invalid characters. |

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

See [verifyUpgradePackage](#verifyupgradepackage)
