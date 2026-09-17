# createHidHostProfile

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## createHidHostProfile

```TypeScript
function createHidHostProfile(): HidHostProfile
```

create the instance of hid profile.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [HidHostProfile](arkts-connectivity-bluetoothmanager-hidhostprofile-i.md) | Returns the instance of hid profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
try {
    let hidHostProfile = hid.createHidHostProfile();
    console.info('hidHost success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
