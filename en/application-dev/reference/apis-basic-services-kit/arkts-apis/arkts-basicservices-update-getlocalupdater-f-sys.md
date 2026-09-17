# getLocalUpdater (System API)

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getLocalUpdater

```TypeScript
function getLocalUpdater(): LocalUpdater
```

Obtains a **LocalUpdater** object, which is used to upgrade the system from a local storage device (such as the SD card). After this API is called, the system returns the **LocalUpdater** utility object, which provides functions such as verifying and installing the local upgrade package.

The typical process is as follows: The developer prepares the upgrade package (in .zip or .bin format) and certificate file (in .cert or .der format). The system verifies the package signature and integrity. The system installs the upgrade package. The system restarts to apply the new version.

**Overview**

This API obtains a **LocalUpdater** object and encapsulates the capabilities of verifying the upgrade package (the digital signature, file integrity, and version compatibility) and installing the upgrade package (decompress the package and writing it to the system partition). The local upgrade does not depend on the network. The upgraded package is read from the device.

**Constraints**

- The upgrade package must be downloaded from the official website of the vendor or from an official channel to  
ensure that the source is trusted.  
- Before the installation, you must verify the upgrade package by calling **verifyUpgradePackage**. An unverified  
package may damage the system.  
- During the upgrade, the device automatically restarts. The app status needs to be saved.  
- The **ohos.permission.UPDATE_SYSTEM** permission is required for calling **getLocalUpdater** APIs.  
- The upgrade package file path contains a maximum of 255 characters. If the value contains more than 255  
characters, an exception is thrown.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [LocalUpdater](arkts-basicservices-update-localupdater-i-sys.md) | Utility object used to perform local update operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Obtain a LocalUpdater object.
  let localUpdater = update.getLocalUpdater();
```
