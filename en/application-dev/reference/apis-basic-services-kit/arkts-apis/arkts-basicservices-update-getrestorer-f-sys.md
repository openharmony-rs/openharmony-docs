# getRestorer (System API)

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## getRestorer

```TypeScript
function getRestorer(): Restorer
```

Obtains a **Restorer** object for restoring factory settings. After this API is called, the system returns the **Restorer** utility object. Three factory reset methods are provided:

- **factoryReset**: Common factory reset. Only data in the user partition is cleared in this mode. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md).  
- **forceFactoryReset**: Forcible factory reset. Both data in the user partition and file keys are cleared in this  
mode. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md).  
- **deepFactoryReset**: Deep factory reset. Data in the scope specified by **scope** is cleared in this mode.  
**DATA**: Clear data in the user partition only; **DATA_AND_OS**: Clear data in both the user partition and OS partition. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md).

After obtaining the object, you can call the corresponding method to restore the device to its factory settings. The device will restart and restore to its initial factory settings.

**Overview**

This API obtains a **Restorer** object through the system service interface, and encapsulates core functions such as data partition clearing, key clearing, and system partition clearing.

**Constraints**

- Restoring factory settings is irreversible and will permanently delete user data. Therefore, remind users to back  
up important data in advance.  
- The **ohos.permission.FACTORY_RESET** permission is required for calling **factoryReset**, **deepFactoryReset**,  
and **getDeepFactoryResetInfo**.  
- The **ohos.permission.FORCE_FACTORY_RESET** permission is required for calling **forceFactoryReset**.  
- During the operation, the device automatically restarts. The app status needs to be saved.  
- **deepFactoryReset** takes a long time (1 to 4 hours depending on the device storage capacity). Ensure that the  
device has sufficient battery power (recommended battery level:  
> 50%).
- You are advised to perform the factory reset operation after clicking the confirmation button in the dialog box  
or on the screen.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Restorer](arkts-basicservices-update-restorer-i-sys.md) | Utility object used to perform factory reset operations. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Obtain a Restorer object for restoring factory settings.
  let factoryRestorer = update.getRestorer();
```
